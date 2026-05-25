---
title: "Keys and secrets"
summary: "When you install a code agent on your system, you are basically inviting a guest into your house, and trusting that said guest doesn't take your keys or credit cards, or tells outsiders where your keys are, or what your credit card information is."
date: 2026-05-18
categories: ["Project", "Exam"]
tags: ["keys", "secrets"]
---

## Risks with code agents

When you install a code agent on your system, you are basically inviting a guest into your house, and trusting that said guest doesn't take your keys or credit cards, or tells outsiders where your keys are, or what your credit card information is.

Likewise, when you give code agents access to your system, or just a sandbox of your system, it is uncertain what the code agent will do with that access. We will never have full control over what the agent might do with its access rights, but we have to put our trust in the agent, that it won't have malicious intent, when we ask for its help.

With code agents however, you increase the risks of such keys and secrets being leaked because code agents might:

- Train on the data that it reads from your system
- Log or document your keys and secrets to files that are not ignored by git

## What can we do about it?

For starters, storing keys and secrets in a file does not make it inherently secret. It is just plain text in a file. On the other hand, the program can't run without access to the keys and secrets, so how do we overcome this issue?

### 1. Never hard code your keys and secrets

Even without the use of AI, hardcoding your secrets is the most criminal act you could commit. If your repository is public or gets leaked, you immediately hand over those hard coded keys and secrets for everyone to see.

### 2. Restrict `.env` to local environment only

Having keys and secrets to your local environment stored in a `.env` or `.config` is still a perfectly valid solution. After all, you need to run your local environment somehow. This does not prevent a code agent from leaking your keys and secrets, but local keys and secrets are less valuable for a bad actor.

### 3. Use a vault

For production environment, store the keys and secrets in a **secure vault**:

- AWS Secrets Manager
- Azure Key Vault
- HashiCorp Vault

A vault is a cloud service for securely storing and accessing keys, secrets, passwords and certificates.

You can use a vault to store all your production keys and secrets, where AI don't have access. When you deploy or run your production environment, you can inject the keys and secrets, either through a CI/CD pipeline, or at runtime.

## What we've learned

- Code agents introduces a potentially higher risk of leaking your keys and secrets
- Only use local keys and secrets in your `.env` or `.config` file, and make sure that they are excluded in version control
- Take precautions when using AI in your project. Limit what access you give the AI, and do not store production keys and secrets in your source code or project folder
- Separate production keys and secrets from the code, and store them in a key vault