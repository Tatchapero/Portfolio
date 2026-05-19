---
title: "Customer case"
summary: "Today I had the pleasure of meeting a pair of estate owners, that runs a business of arranging weddings, Christmas markets, and other events at their estate. They presented their current setup that their company uses to keep track of progress of individual events, and with that, the issues that comes with the current solution they are using. Their company primarily uses Trello as progress board, but a lot of their processes and workflows are time consuming and manual labour. A little automation or use of AI could probably help them with some of their burdens. And that's where we come in."
date: 2026-05-04
categories: ["Project", "Exam"]
tags: ["customer", "case"]
---

## Customer case

Today I had the pleasure of meeting a pair of estate owners, that runs a business of arranging weddings, Christmas markets, and other events at their estate.

They presented their current setup that their company uses to keep track of progress of individual events, and with that, the issues that comes with the current solution they are using. Their company primarily uses Trello as progress board, but a lot of their processes and workflows are time consuming and manual labour. A little automation or use of AI could probably help them with some of their burdens. And that's where we come in.

### Meeting Summary

To keep the customers names anonymous, they have been renamed to "*Mr. J*".

Here's a summary of the meeting:

{{< accordion mode="open" separated=true >}}
    {{< accordionItem title="Summary" md=true >}}

## Pains
- A large amount of time is spent managing weddings and large parties during the summer season.
- Conferences are difficult to host because there are not enough sleeping accommodations.
- Guests have limited transportation options since no buses go to the estate.
- Creating contracts from Trello boards is the biggest time-consuming task.
- Contracts are manually created in Word documents based on information entered into the bookkeeping/accounting system.
- Employees must manually follow up with customers to collect missing information.
- Inventory is counted manually twice a year and entered into Excel sheets.
- Vendor communication for the Christmas market is handled manually through PDFs and emails.
- Stall placement requests for the Christmas market are handled manually.
- There is no automated way to compare menus against available inventory and ingredient requirements.

---

## Wishes
- Automate the process of generating contracts from Trello boards.
- Automate reminders to customers who have not submitted required information.
- Create a system that converts menus into ingredient requirements.
- Compare ingredient requirements against current inventory levels automatically.
- Optimize purchasing to reduce waste and save money on ingredients and materials.
- Automatically send reminder emails to Christmas market vendors 14 days before the event.
- Improve management of vendor stall requests and placement.
- Streamline event management workflows across weddings, conferences, and rentals.

---

## Nouns
- Estate / Manor
- Wedding barn
- Restaurant building
- Weddings
- Large parties
- Confirmations
- Birthdays
- Conferences
- Sleeping rooms
- Glamping tents
- Summer houses
- Contracts
- Agreements
- Bookkeeping system
- Word document
- Offer / Quote
- Invoice
- Trello board
- Wedding template
- Summer house rental board
- Customers
- Employees
- Decorations
- Flowers
- Food
- Beverages
- Inventory
- Excel sheet
- Menus
- Ingredients
- Christmas market
- Vendors / Stallholders
- PDF
- Reminder emails
- Train connection
- Copenhagen (CPH)

---

## Glossary

| Danish Term      | English Translation  | Meaning                                        |
| ---------------- | -------------------- | ---------------------------------------------- |
| Lade             | Barn                 | Large event barn used for weddings and parties |
| Godset           | Estate / Manor       | The property hosting events and accommodations |
| Bryllup          | Wedding              | Main event type handled by the business        |
| Konfirmation     | Confirmation         | Religious/family celebration event             |
| Tilbud           | Quote / Offer        | Proposal sent to customers                     |
| Faktura          | Invoice              | Billing document sent after agreement          |
| Bogføringssystem | Bookkeeping system   | Financial/quotation management system          |
| Sommerhus        | Summer house         | Rental accommodation                           |
| Standeholder     | Vendor / Stallholder | Participant in the Christmas market            |
| Julemarked       | Christmas market     | Seasonal event with vendors                    |
| Lager            | Inventory / Stock    | Stored ingredients and materials               |

---

## Activity Diagram

```
Customer Inquiry
    ↓
Customer sends email asking for pricing and availability
    ↓
Mr. J sends standard response with attached pricing documents
    ↓
(Optional) Customer visits the estate
    ↓
Mr. J enters offer details into bookkeeping system
    ↓
Mr. J manually updates Word contract/offer document
    ↓
Offer is sent to customer
    ↓
Customer signs agreement
    ↓
Estate sends invoice
    ↓
Event planning tasks managed in Trello
    ↓
Employees complete event-specific tasks
    ↓
Follow-up reminders sent for missing customer information
    ↓
Final contract generated from Trello board
    ↓
Event execution
```

---

## Communication Routes
### Wedding & Event Booking
```
Customer
    ↔ Email ↔
Mr. J
    ↔ Bookkeeping System ↔
Offer / Contract Documents
    ↔ Invoice ↔
Customer
```

### Internal Event Coordination
```
Mr. J
    ↔ Trello Board ↔
Employees
```

### Customer Follow-up
```
Mr. J
    ↔ Reminder Emails ↔
Customers
```

### Christmas Market Vendor Management
```
Estate
    ↔ PDF / Email ↔
Vendors / Stallholders
    ↔ Placement Requests ↔
Estate
```

### Inventory & Kitchen Planning
```
Menus
    ↔ Ingredient Requirements ↔
Inventory System / Excel
    ↔ Purchasing Decisions ↔
Suppliers
```

    {{< /accordionItem >}}
{{< /accordion >}}

## Suggestions

Here are a couple of ideas, where AI could help our customer:

1. Automatic Contract Generator
    - AI reads Trello data automatically
    - AI generates a Word/PDF
2. Automatic email-flow for customer
    - Automatically send standard reply
    - Automatically remind customers for missing information
3. AI-assistent
    - An internal AI-chat that can find data, generate documents and mails
4. Logistics control and menu optimization
    - Use AI to calculate ingredients, amounts and grocery list
5. Automatic Christmas market management
    - AI collects all data and automatically places stalls
    - AI creates a map of all stalls
6. AI for conferences and booking optimization
    - Automatically suggest overnight stay
    - Booking optimization
    - Suggestions for package-solutions