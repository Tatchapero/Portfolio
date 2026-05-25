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

We'll use a Code Agent to get project up and running, so create a new folder, spin up your agent, go to `/plan` mode and give it this prompt:

```
I want to make a Java application that can retrieve data from the Trello REST API.

Technical requirements:
- Backend must be made in Springboot, Java
- Must use a MVC pattern

Business requirements:
- Backend must be able to retrieve Trello list data
- Trello data must contain task title, task body content, and task status
```

Here's the first draft of what the code agent has created:

{{< github repo="Tatchapero/automatic-contract-generator" showThumbnail=true >}}

We'll follow this up next time with the next step in our battle plan where we'll try to **Extend the Java program to call OpenAI’s API**.