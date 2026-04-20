---
title: "Code Agents"
summary: "Code agents - AI systems that go beyond answering questions to autonomously build and execute tasks. It explains how they differ from traditional assistants, explores different types of agents, and demonstrates their capabilities by creating and deploying a full meditation quiz app from a single prompt."
date: 2026-04-20
categories: ["Project", "Exam"]
tags: ["code", "agent"]
---

## What is a code agent?

There's a distinctive difference between using an AI on a website, and using a Code Agent:

- An assistant is an AI you can *ask anything*
- An agent is an AI that can *do anything*

|  | Assistants | Agents |
| --- | --- | --- |
| Control flow | You control the loop | It controls the loop |
| Time horizon | One-shot ( or short conversations) | Long-running tasks |
| State management | Context = prompt | Context = environment |
| Autonomy | Supports human decisions | Fully autonomous |
| Decision-making | Provides insights for users to act on | Operates independently |
| Complexity | Adapts to user input dynamically | Performs structured tasks

### Horizontal vs Vertical agents

- Horizontal agents: Broad capability across domains (like ChatGPT)
- Vertical agents: Specialized for one domain


### Types of code agents

| Claude Code | OpenAI Codex |
| --- | --- |
| Better imagination. Good for sparring and helping figure out what is wrong or what's going on | Faster and more reliable but needs more concise instructions

## Meditation Quiz App

Let's make a Meditation Quiz App from scratch using a Code Agent, to demonstrate the power of this tool.

### Choose your Code Agent

What you choose is entirely up to you. As stated above, the difference between code agents are minimal, so it is mostly up to personal preferrence.

- [Claude Code Quickstart](https://code.claude.com/docs/en/quickstart)
- [OpenAI Codex Quickstart](https://developers.openai.com/codex/quickstart)

> [!TIP]
> If using the CLI, type `/plan` to switch to Plan mode

Once setup give it the prompt below:

{{< accordion mode="open" separated=true >}}
    {{< accordionItem title="Prompt" md=true >}}

```
I need to make a website called Scenius. It's a meditation quiz app, and it has the following requirements:

Requirements:
- Must be made in React
- User must be able to select a block of questions, that shows the correct answers after finishing the block
- It should be possible to take a quiz again
- A quiz should remember the answers if you have taken it before
- When starting a quiz, it should ask if you want to see your previous answers (if available), or start a new quiz
- Blocks must be answered in order (0 through 4)
- User must answer all questions correctly before proceeding to the next block
- Should be able to create more questions in the future
- Does not rely on a database
- It needs to be deployed (preferably on GitHub as a static website)

Here's the quiz with the correct answers checked:

# 0) Om meditation - og vælge ikke at have et problem

## #1 - Målet med meditation er at være helt tom for tanker

* [ ] Rigtigt
* [x] Forkert

## #2 - Hvor længe skal man meditere?

* [ ] Det er lige meget
* [ ] 20 minutter om dagen
* [x] Så længe man på forhånd har besluttet sig for at gøre det
* [ ] Altid over 10 minutter ad gangen

## #3 - Man kan kun meditere rigtigt hvis man sidder i lotusstilling

* [ ] Rigtigt
* [x] Forkert

## #4 - Meditation er en teknik

* [ ] Rigtigt
* [x] Forkert

## #5 - Hvis jeg opdager, at jeg tænker på et problem, hvad gør jeg så?

* [ ] Gennemgår instruktionerne og vender tilbage til meditationen
* [ ] Tænker på noget andet
* [x] Ingenting - jeg er allerede fri af tankerne
* [ ] Skubber tankerne væk

## #6 - Hvis jeg synes det er svært at meditere, hvad gør jeg så?

* [x] Så vælger jeg ikke at gøre et problem ud af det
* [ ] Så forsøger jeg at tænke på noget positivt
* [ ] Så gør jeg det forkert

---

# 1) Om at være stille

## #1 - At være stille har både en indre og en ydre del

* [x] Rigtigt
* [ ] Forkert

## #2 - Den indre del betyder:

* [x] At jeg ikke forholder mig til tanker og følelser
* [ ] At alle tanker og følelser står stille
* [ ] At jeg kan fjerne alle tanker og følelser
* [ ] At jeg ikke dagdrømmer

## #3 - Man kan ikke være stille når der er larm i nærheden?

* [ ] Rigtigt
* [x] Forkert

## #4 - Man kan godt være fuldkommen stille og samtidig have hovedet fuld af tanker igennem hele meditationen?

* [x] Rigtigt
* [ ] Forkert

## #5 - Man kan kun meditere hvis man sidder fuldkommen stille?

* [ ] Rigtigt
* [x] Forkert

## #6 - Stilhed er ...

* [ ] en følelse
* [ ] en oplevelse
* [ ] en måde at have det på
* [x] en indre position i forhold til tanker og følelser

---

# 2) Om at være afslappet (ease of being)

## #1 - Den indre del af instruktionen er den vigtigste?

* [x] Rigtigt
* [ ] Forkert

## #2 - Det indre og ydre afspejler hinanden i meditationen. Hvad betyder det?

* [ ] Hvis man ser anstrengt ud i ansigtet, så har man psykiske problemer
* [ ] At hvis man smiler, så virker meditationen bedre
* [ ] At hvis der er fred på ydersiden, så er der også fred på indersiden
* [x] At hvis man er afslappet på ydersiden, er det lettere at være afslappet på indersiden og omvendt

## #3 - Det gælder om at blive mere og mere afslappet i kroppen i løbet af meditationen?

* [ ] Rigtigt
* [x] Forkert

## #4 - At være afslappet i forhold til sin oplevelse betyder, at vi

* [x] ikke blander os i hvad vi oplever
* [ ] observerer vores tanker og skubber dem væk
* [ ] ikke må føle noget når vi mediterer

## #5 - Meditation virker ikke hvis man er anspændt i kroppen

* [ ] Rigtigt
* [x] Forkert

## #6 - Hvis jeg er helt afslappet i kroppen efter en meditation er det et tegn på at jeg har gjort det rigtigt?

* [ ] Rigtigt
* [ ] Forkert
* [x] Måske

---

# 3) Om at være opmærksom og lysvågen

## #1 - I denne meditationsform retter man sin opmærksomhed mod objekter i bevidstheden

* [ ] Rigtigt
* [x] Forkert

## #2 - Objekter i bevidstheden er:

* [ ] Tanker, følelser og lyde
* [x] Alt som har en begyndelse og en afslutning
* [ ] Tanker og genstande

## #3 - Man kan ikke småsove og være opmærksom på samme tid?

* [x] Rigtigt
* [ ] Forkert

## #4 - At være opmærksom i meditation er ...

* [ ] at være opmærksom på alt, der rører sig i bevidstheden
* [x] ikke at hænge fast i noget
* [ ] at være fast fokuseret på et punkt

## #5 - Når man er opmærksom er der ingen tanker?

* [ ] Rigtigt
* [x] Forkert

## #6 - Man skal anstrenge sig for at være opmærksom?

* [ ] Rigtigt
* [ ] Forkert
* [x] Hverken rigtigt eller forkert

---

# 4) Om at lade alting være

## #1 - Hvis man overholder den første instruktion og er fuldkommen stille, så lader man også alting være?

* [x] Rigtigt
* [ ] Forkert

## #2 - Du er dine tanker og følelser?

* [ ] Rigtigt
* [x] Forkert

## #3 - At lade alting være, som det er, er det samme som at vælge ikke at have et problem?

* [x] Rigtigt
* [ ] Forkert

## #4 - At lade alting være som det er, betyder at man først og fremmest skal lade de negative tanker være?

* [ ] Rigtigt
* [x] Forkert

## #5 - Når vi lader ALTING være, så har vi droppet vores relation til alt bevidsthedsindhold

* [x] Rigtigt
* [ ] Forkert

Do you need any clarifications?

```

    {{< /accordionItem >}}
{{< /accordion >}}

### Results

The prompt states that it must be deployed, and as such, it should provide a GitHub Actions workflow to let you deploy it - Just remember to go to your project settings on GitHub, then the **Pages** side menu, and change your **Source** to `GitHub Actions`.

Check it out here: {{< icon "link" >}} [Scenius](https://tatchapero.github.io/Scenius/)

## What we've learned

- The difference between an AI Assistant and a Code Agent
- Which Code Agents exists today and their pros & cons
- How to build a quiz app using a code agent