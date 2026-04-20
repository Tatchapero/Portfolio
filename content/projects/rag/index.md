---
title: "RAG"
summary: "RAG (Retrieval Augmented Generation) is an AI technique that improves answers by combining information retrieval from external sources with language model generation. It helps overcome limitations of standard models by providing up-to-date, accurate, and context-specific responses."
date: 2026-04-13
categories: ["Project", "Exam"]
tags: ["rag", "chunk", "vector", "embedding"]
---

## What is RAG?

Retrieval Augmented Generation. A technique used in AI to improve answers by combining:
- **Retrieval**: The system looks up relevant information from external sources (documents, databases, PDFs, websites, internal company data)
- **Generation**: The language model uses the retrieved information to generate a response

Normal AI models rely only on what they were trained on. With RAG, the AI can provide up-to-date info, granted they are provided with new information. They are not limited by a models training cutoff. This means it can provide more accurate answers that are grounded in real data. 

At its core, RAG solves a fundamental limitation, that LLM's (Large Language Models) don't know your data. LLM's are trained on general data, and can therefore be outdated, hallucinate, and most importantly they don't have access to private or internal information.

## How does it work?

### 1. Ingestion

Prepare your knowledge base and collect any data you can feed the RAG (PDFs, docs, webpages, databases, API's etc.), and **chunk** the data into smaller pieces. LLM's can't process huge amounts of documents at once, and smaller chunks improves retrieval accuracy.

### 2. Embedding

Each chunk is converted into a **vector** (a list of numbers representing meaning).

Example:

```
"Denmark has a strong welfare system"
→ [0.12, -0.98, 0.44, ...]
```

This is done using an **embedding model**.

The key idea of doing this, is that similar meanings will have similar vectors. This enables semantic search, and not just a keyword matching.

### 3. Storage (vector database)

All embeddings are stored in a **vector database**. This allows for fast similarity search like

> "Find chunks most similar to this question"

### 4. Query

When a user asks a question like: 

> "What are the benefits of Denmark's welfare system?"

The RAG then converts the question to an embedding, so that it can make a vector representation. The system then finds the _closest vectors_ in the vector database, and could retrieve something like:

> "Denmark provides universal healthcare..."

### 5. Augmentation

The retrieved chunks are inserted into the prompt:

```
Answer the question using the context below:

[Chunk 1]
[Chunk 2]
[Chunk 3]

Question: What are the benefits of Denmark’s welfare system?
```

### 6. Generation (LLM response)

The model can now read the retrieved context, and generate an answer that is grounded in it.

## Create a RAG chatbot

1. Create an account at [Dify.ai](https://cloud.dify.ai/signin)
2. Sign in

### Provide knowledge

1. Navigate to the `Knowledge` tab
2. Select `Create Knowledge`
3. Select `Import from file` and upload a file (or use the file below)

<a class="btn" href="/Portfolio/files/Resume.md" download>Download</a>

4. Once uploaded, click `Next`
5. Set `Retrieval Setting` to **Hybrid Search**
6. Save & Process

### Create the chatbot

1. Navigate to the `Studio` tab
2. In the `CREATE APP` card, select `Create from Blank`
3. Expand the `MORE BASIC APP TYPES` and select `Chatbot`
4. Provide a name and `Create`
5. Provide some intructions (or use the instructions below)

{{< accordion >}}
  {{< accordionItem title="Instructions" open=false >}}
  You are a helpful assistant that answers questions about the person described in the provided CV and supporting context.

Your role:
- Help users quickly find accurate information about this person.
- Be supportive, professional, and easy to talk to.
- Act like an assistant for this person, not as the person.

Behavior:
- Give short, clear, and concise answers.
- Prefer direct answers over long explanations.
- Be friendly and helpful.
- Summarize when possible.
- Use bullet points only when they improve clarity.

Grounding:
- Only answer using information found in the provided CV or retrieved context.
- Do not invent details, infer personal facts, or guess.
- If the answer is not in the context, say so briefly and suggest what kind of information is available.

Response rules:
- Keep answers brief unless the user asks for more detail.
- Focus on facts such as experience, skills, education, projects, achievements, roles, and background.
- When relevant, mention that the answer is based on the available CV/context.
- If multiple relevant facts exist, give the most important ones first.

Tone:
- Supportive
- Professional
- Concise
- Helpful

Examples:
- If asked "What are his main skills?" give a short list of the most relevant skills from the CV.
- If asked "What experience does he have in X?" summarize only the experience supported by the context.
- If asked something not covered in the CV, respond: "I could not find that in the available CV/context."

Do not:
- Pretend to have personal knowledge beyond the provided documents.
- Make up dates, titles, achievements, or opinions.
- Give long or repetitive answers.
  {{< /accordionItem >}}
{{< /accordion >}}

6. In `Knowledge` section, click `+ Add`
7. Select the file you uploaded and click `Add`
8. Click `Publish` in top right corner and then `Publish Update`
9. Ask the bot anything that it might be able to answer from the knowledge provided

## What we've learned

- What is a RAG, and how does it work
- How to create a simple chatbot