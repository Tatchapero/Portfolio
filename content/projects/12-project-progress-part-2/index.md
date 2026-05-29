---
title: "Project progress PART 2"
summary: "To re-iterate on what the next 3 steps are in the current plan, it is: 1. A Java program that can call the Trello API. 2. Extend the Java program to call OpenAI’s API. 3. Test the quality of the generated contracts. And today we're going to be looking making a Java program that can call the Trello API."
date: 2026-05-18
categories: ["Project", "Exam"]
tags: ["project", "progres", "part", "two"]
---

## Battle plan

To re-iterate on what the next 3 steps are in the current plan, it is:

1. A Java program that can call the Trello API  
2. Extend the Java program to call OpenAI’s API
3. Test the quality of the generated contracts

And today we're going to be looking making a Java program that can call the Trello API.

## The backend

First, we'll have to create a back-end. For this, I've chosen to go with a language I know - Java. The easiest way to get started, will be to start a Springboot project. Springboot comes with a lot of tools that can shave off a lot of the boiler plate code. This will make it easier to work with and maintain.

Secondly, we'll have to decide how we want to structure our project. I always opt for an MVC (Model, View, Controller) pattern, since it organizes the different patterns into their own folders.

We'll use a Code Agent to get project up and running, so create a new folder, spin up your agent, go to `/plan` mode and give it these prompts:

```
I want to make a Java application that can retrieve data from the Trello REST API.

Technical requirements:
- Backend must be made in Springboot, Java
- Must use a MVC pattern

Business requirements:
- Backend must be able to retrieve Trello list data
- Trello data must contain task title, task body content, and task status
```

```
Add a new feature that can retrieve a list of Trello lists.

  Requirements:
  - The code must call the Trello API and return a list of Trello lists with:
    - List id
    - List name
  - The list ID's must be stored in temporary memory until the program ends (Do not use a database, and do not use
  system IO)
  - The SPEC.md must be updated (if relevant)
  - The README.md must be updated (if relevant)
```

```
I want to change the /tasks endpoint to POST, and accept a trello list ID

  Requirements:
  - Change /tasks endpoint to POST
  - /tasks endpoint must now accept a Trello list ID
  - The /tasks endpoint will use the provided ID, instead of the application.properties or .env file
  - Refactor and clean up the code to accomodate for the new change
  - Update the src\main\resources\demo.http to use "6a17f457ff75190922a9e893" as Trello list ID for testing "1) Get
  tasks"
  - Remember to update SPEC.md (if necessary)
  - Remember to update README.md (if necessary)
```

We'll follow this up next time with the next step in our battle plan where we'll try to **Extend the Java program to call OpenAI’s API**.