---
title: "Project progress PART 1"
summary: "Placeholder"
date: 2026-05-11
categories: ["Project", "Exam"]
tags: ["project", "progres", "part", "one"]
---

## Pre-planning

Before we begin building the project, we should have a battle plan: What should we name the project, what's the core issue, etc.

### **Project Working Title**  
- Automatic Contract Generator

#### **Problem**  
- Compiling the contract based on Trello tasks is a time consuming manual task

#### **User**  
- Mr. J

#### **Current Process**  
1–2 months before a wedding, when all tasks in a Trello column are green (DONE), Mr. J takes the information from all the tasks and copies it into a contract.

1. Extract data from Trello  
2. Find the following data:
   - Number of guests
   - Menu
   - Beverages
   - Flowers
   - Location
   - Times
   - Accommodation
   - Special requests
   - Prices

3. Compile a contract:
   - Customer information
   - Date
   - Menu
   - Prices
   - Payment terms
   - Schedule
   - Additional services

4. Approve contract  
5. Send offer

### **Proposed Solution**  
- A full-stack web application that can call the Trello API, retrieve data, and forward it to an AI REST API, which generates a Word/PDF document that can be previewed and downloaded from the user interface.

#### **AI Functionality**  
- AI is used to generate the contract in Word/PDF format

#### **MVP**  
A REST API that can receive a POST request with data and return a contract in Word/PDF format.

#### **Scope Limitation**  
A custom-built solution that can only retrieve data from a single Trello board.

#### **Customer Questions**  
- What does a Trello board look like when all data is ready to generate a contract?
- What does a final contract look like?
- Which data is transferred from the Trello board to the contract?

#### **Assumptions**  
- That they want a third-party website to generate their contracts.

### **Next Three Tasks**  
1. A Java program that can call the Trello API  
2. Extend the Java program to call OpenAI’s API
3. Test the quality of the generated contracts