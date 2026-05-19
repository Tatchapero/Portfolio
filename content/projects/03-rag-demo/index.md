---
title: "Automate RAG"
summary: "This project shows you how to fully automate your chatbot’s knowledge so it never falls behind. Every time you publish new content, your chatbot instantly learns it—no manual updates, no maintenance headaches."
date: 2026-04-13
categories: ["Project", "Exam"]
tags: ["automation", "rag", "rest"]
---

## Automate RAG

This is a continuation of the RAG article. If you haven't checked it out yet, I highly recommend giving it a read, since we are building upon another project:

{{< article link="/Portfolio/projects/rag/" showSummary=true compactSummary=true >}}

### Goal

The ultimate goal is to make a RAG chatbot that continously improves its knowledgebase, the moment the information is available. To do this, we make a RAG that retrieves the articles from this website. As soon as a new article is released, the chatbot needs to know about it

### Solution

There are many ways to approach this problem, but the simplest solution that works on any Hugo/Blowfish site, is a simple script and a few changes to the GitHub workflow file. Here's the idea:

- Use Dify.ai's API endpoint to provide the knowledge
- Call the endpoint on each deploy
- Wipe the entire knowledge base, and rebuild it on every deploy

Hugo and Blowfish website articles are markdown files. We can send these files to the Dify.ai using their API Rest endpoint. What we need are a Dify.ai:

- Base URL
- API key
- Dataset ID

And here's how we're going to do it:

1. Login to your Dify.ai account and open the **Knowledge** tab
2. Click on the **Service API** button. Here's the **Base URL** `https://api.dify.ai` (omit the `/v1`)
3. Click on the **API Key** and then **Create new Secret key**
4. Copy the key and write it down somewhere. You will **not** be able to view it again
5. Open the **Knowledge** base you want to use
6. In the URL, there should be a UUID/GUID. This is your **Dataset ID**

With all of this, we can now create a GitHub Actions workflow file, that uses this information to send our markdown files to Dify.ai:

{{< accordion mode="open" separated=true >}}
    {{< accordionItem title="hugo.yaml" md=true >}}
```yaml
name: Build and deploy
on:
  push:
    branches:
      - main
  workflow_dispatch:
permissions:
  contents: read
  pages: write
  id-token: write
concurrency:
  group: pages
  cancel-in-progress: false
defaults:
  run:
    shell: bash
jobs:
  build:
    runs-on: ubuntu-latest
    env:
      DART_SASS_VERSION: 1.99.0
      GO_VERSION: 1.26.1
      HUGO_VERSION: 0.160.0
      NODE_VERSION: 24.14.1
      TZ: Europe/Oslo
      DIFY_BASE_URL: ${{ secrets.DIFY_BASE_URL }}
      DIFY_API_KEY: ${{ secrets.DIFY_API_KEY }}
      DIFY_DATASET_ID: ${{ secrets.DIFY_DATASET_ID }}
    steps:
      - name: Checkout
        uses: actions/checkout@v6
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Go
        uses: actions/setup-go@v6
        with:
          go-version: ${{ env.GO_VERSION }}
          cache: false
      - name: Setup Node.js
        uses: actions/setup-node@v6
        with:
          node-version: ${{ env.NODE_VERSION }}
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v6
      - name: Create directory for user-specific executable files
        run: |
          mkdir -p "${HOME}/.local"
      - name: Install Dart Sass
        run: |
          curl -sLJO "https://github.com/sass/dart-sass/releases/download/${DART_SASS_VERSION}/dart-sass-${DART_SASS_VERSION}-linux-x64.tar.gz"
          tar -C "${HOME}/.local" -xf "dart-sass-${DART_SASS_VERSION}-linux-x64.tar.gz"
          rm "dart-sass-${DART_SASS_VERSION}-linux-x64.tar.gz"
          echo "${HOME}/.local/dart-sass" >> "${GITHUB_PATH}"
      - name: Install Hugo
        run: |
          curl -sLJO "https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz"
          mkdir "${HOME}/.local/hugo"
          tar -C "${HOME}/.local/hugo" -xf "hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz"
          rm "hugo_extended_${HUGO_VERSION}_linux-amd64.tar.gz"
          echo "${HOME}/.local/hugo" >> "${GITHUB_PATH}"
      - name: Verify installations
        run: |
          echo "Dart Sass: $(sass --version)"
          echo "Go: $(go version)"
          echo "Hugo: $(hugo version)"
          echo "Node.js: $(node --version)"
      - name: Install Node.js dependencies
        run: |
          [[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true
      - name: Configure Git
        run: |
          git config core.quotepath false
      - name: Install jq
        run: |
          sudo apt-get update
          sudo apt-get install -y jq
      - name: Sync Hugo markdown to Dify
        run: |
          set -euo pipefail

          : "${DIFY_BASE_URL:?Missing DIFY_BASE_URL}"
          : "${DIFY_API_KEY:?Missing DIFY_API_KEY}"
          : "${DIFY_DATASET_ID:?Missing DIFY_DATASET_ID}"

          echo "Deleting existing Dify documents..."
          page=1

          while :; do
            response=$(curl --silent --show-error --fail \
              --request GET \
              --url "${DIFY_BASE_URL}/v1/datasets/${DIFY_DATASET_ID}/documents?page=${page}&limit=100" \
              --header "Authorization: Bearer ${DIFY_API_KEY}")

            ids=$(echo "$response" | jq -r '.data[]?.id')
            has_more=$(echo "$response" | jq -r '.has_more // false')

            if [ -n "$ids" ]; then
              while IFS= read -r id; do
                [ -z "$id" ] && continue
                echo "Deleting document ${id}"
                curl --silent --show-error --fail \
                  --request DELETE \
                  --url "${DIFY_BASE_URL}/v1/datasets/${DIFY_DATASET_ID}/documents/${id}" \
                  --header "Authorization: Bearer ${DIFY_API_KEY}"
              done <<< "$ids"
            fi

            if [ "$has_more" != "true" ]; then
              break
            fi

            page=$((page + 1))
          done

          echo "Uploading Hugo markdown files..."
          find content -type f -name "*.md" | sort | while IFS= read -r file; do
            # Create unique name from path
            doc_name=$(echo "$file" \
              | sed 's#^content/##' \
              | sed 's#/index.md$##' \
              | sed 's#\.md$##' \
              | sed 's#/#__#g')

            echo "Uploading ${file} as ${doc_name}"

            curl --silent --show-error --fail \
              --request POST \
              --url "${DIFY_BASE_URL}/v1/datasets/${DIFY_DATASET_ID}/document/create-by-file" \
              --header "Authorization: Bearer ${DIFY_API_KEY}" \
              --form "file=@${file};filename=${doc_name}.md" \
              --form 'data={"indexing_technique":"high_quality","doc_form":"text_model","process_rule":{"mode":"automatic"}}'
          done
      - name: Cache restore
        id: cache-restore
        uses: actions/cache/restore@v5
        with:
          path: ${{ runner.temp }}/hugo_cache
          key: hugo-${{ github.run_id }}
          restore-keys:
            hugo-
      - name: Build the site
        run: |
          hugo build \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/" \
            --cacheDir "${{ runner.temp }}/hugo_cache"
      - name: Cache save
        id: cache-save
        uses: actions/cache/save@v5
        with:
          path: ${{ runner.temp }}/hugo_cache
          key: ${{ steps.cache-restore.outputs.cache-primary-key }}
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v5
```
    {{< /accordionItem >}}
{{< /accordion >}}

Once added, you should push this to your GitHub project, and the CI/CD pipeline should start, however it will fail because we need to provide the base URL, API key, and dataset ID as secrets.

1. Open your project settings on GitHub
2. Open **Secrets and variables**, then **Actions** on the left menu
3. Add 3 new repository secrets:

    - `DIFY_BASE_URL`
    - `DIFY_API_KEY`
    - `DIFY_DATASET_ID`

It is important, that you write secret names exactly like this - Otherwise the GitHub Actions will not detect these secrets.

### What we've learned

- How to automatically feed the RAG more knowledge
- Using Dify.ai API REST endpoint