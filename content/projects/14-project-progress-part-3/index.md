---
title: "Project progress PART 3"
summary: "Today the plan is to hook up our backend to an LLM API. We'll be using the LLM API to generate a contract as a Word/PDF. To do that, we'll provide the Trello data, along with a contract template for the LLM API to build our contract."
date: 2026-05-22
categories: ["Project", "Exam"]
tags: ["project", "progres", "part", "three"]
---

## Connecting to an LLM API

Today the plan is to hook up our backend to an LLM API. We'll be using the LLM API to generate a contract as a Word/PDF. To do that, we'll provide the Trello data, along with a contract template for the LLM API to build our contract. Here's the prompt to get started:

```
Create a new feature, that takes the Trello data from the /api/tasks endpoint, and the
  src\main\java\com\automaticcontractgenerator\template\contract.md and sends it to OpenAI's LLM API, and asks it to
  fill the contract with the Trello data.

  Requirements:
  - The LLM API integration must be using OpenAI's API
  - You must create a System Prompt in markdown and put it in a folder named "prompts"
  - You must create a User Prompt in markdown and put it in a folder named "prompts"
  - The System Prompt must ask the LLM to:
    - Create a contract for a wedding
    - Create the contract, and return it as a base64 encoded PDF
    - To remove all instances of pricing from the contract
  - The User Prompt must contain a contract template with the following sections in danish:
    - Date
    - Menu
    - Time schedule
    - Extra services
    - Signatures (Customer)
    - Signatures (Supplier)
  - The LLM API must return the contract as a PDF
  - You must update the SPEC.md (if necessary)
  - You must update the README.md (if necessary)
```

## Refactoring

Unfortunately, relying on the LLM API to generate a base64 encoded PDF has turned out to be a failure. The PDF's that we receive are corrupted or invalid, so we'll have to change our plans.

Instead, we'll ask the LLM API to assemble our contract, return it, and then we'll build the PDF ourselves, but we'll have to refactor our code. 

```
Refactor the code to make the OpenAI LLM API return a contract instead of a base64 encoded pdf, and then take the
contract from the response and make it into a pdf. 

Requirements:
- The LLM API may no longer return a base64 encoded PDF
- The LLM API must now return a contract
- The LLM API must include all the information from Trello in the contract, except prices
- Extend the src\main\resources\demo.http to have tests for the new endpoints
- Update the SPEC.md if necessary
- Update the README.md if necessary
```

Next time we'll build our frontend.