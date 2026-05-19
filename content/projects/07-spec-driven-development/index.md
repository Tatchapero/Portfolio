---
title: "Spec-Driven Development"
summary: "Specification-Driven Development (or Spec-Driven Development) is an approach, where the spec is used as the primary artifact to develop the software. A spec is a document that contains the product requirements."
date: 2026-05-01
categories: ["Project", "Exam"]
tags: ["spec", "driven", "development"]
---

## SDD

Specification-Driven Development (or Spec-Driven Development) is an approach, where the spec is used as the primary artifact to develop the software. A spec is a document that contains the product requirements.

There are various approaches to using a spec:

- **Spec-first**: Write a spec, build a feature, then toss the spec
- **Spec-anchored**: Write a spec, build a feature, then update the spec, when the feature needs to be changed
- **Spec-as-source**: Write a spec, and then use AI to depend entirely on building the whole application - Never code anything yourself


### Vibe Coding vs. SDD

But what's the difference between Spec-Driven Development and Vibe Coding?

They are two very different ways of building software:

- Vibe coding is an informal term for coding by intuition and iteration rather than detailed planning
- Spec-Driven Development starts from explicit requirements and system design before implementation


| Aspect            | Vibe Coding         | Spec-Driven Development |
| ----------------- | ------------------- | ----------------------- |
| Planning          | Minimal             | Extensive               |
| Speed             | Very fast initially | Slower upfront          |
| Flexibility       | High                | Moderate                |
| Maintainability   | Often lower         | Usually higher          |
| AI usage          | Heavy improvisation | Structured prompting    |
| Best for          | Exploration         | Scaling                 |
| Documentation     | Sparse              | Explicit                |
| Architecture      | Emergent            | Intentional             |
| Testing           | Often afterthought  | Usually planned         |
| Team coordination | Harder              | Easier                  |

You could say that Vibe Coding is the **Le Bricoleur**, while Spec-Driven development is the **Engineer**. 

However, it is important to note, that one is not better than the other. Each one has their own various use cases where they excel. Vibe Coding is optimized for speed, so it's great for quick demos and Hackathons, while Spec-Driven Development is more optimized for stability, longevity, and scalability.

## SDD Artifact Template

Here's an example of a Spec-Driven Development Artifact Template:

{{< accordion mode="open" separated=true >}}
    {{< accordionItem title="SDD Template" md=true >}}
```
# Spec: <Feature / System / Capability Name>

## 1. Overview

### Purpose
Describe what this spec is for and why it exists.

### Background
Provide relevant context, current limitations, business need, user pain, or technical motivation.

### Goals
- 
- 
- 

### Non-Goals
Things explicitly out of scope:
- 
- 

---

## 2. Users and Use Cases

### Primary Users
- 

### User Needs
- As a <user>, I need <capability>, so that <outcome>.

### Key Use Cases
1. 
2. 
3. 

---

## 3. Requirements

### Functional Requirements
| ID | Requirement | Priority | Notes |
|---|---|---|---|
| FR-001 |  | Must / Should / Could |  |
| FR-002 |  |  |  |

### Non-Functional Requirements
| ID | Requirement | Target / Constraint |
|---|---|---|
| NFR-001 | Performance |  |
| NFR-002 | Security |  |
| NFR-003 | Accessibility |  |
| NFR-004 | Reliability |  |
| NFR-005 | Observability |  |

---

## 4. User Experience / Workflow

### Current Flow
Describe the existing user or system flow.

### Proposed Flow
Describe the new flow step by step.

1. 
2. 
3. 

### Edge Cases
- 
- 
-

## 5. System Behavior

### Inputs
| Input | Source | Validation
| --- | --- | --- |
| | |

### Outputs
| Output | Consumer | Format |
| --- | --- | --- |
| | |

### Business Rules
| Rule ID | Rule |
| --- | --- |
| BR-001 | |
| BR-002 | |

---

## 6. Data and Integrations

### Data Model
Describe new or changed entities, fields, or relationships.

| Entity | Field | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| | | | |

## Integrations
| System | Direction | Purpose | Notes |
| --- | --- | --- | --- |
| | Inbound/Outbound | | |

---

## 7. Technical Design

### Architecture Summary
Describe the proposed architecture at a high level.

### Components
| Component | Responsibility | Owner |
| --- | --- | --- |
| | | |

### API/Interface Changes

METHOD /endpoint

Request:
{}

Response:
{}

### Dependencies
-
-

---

## 8. Implementation Plan

### Milestones
| Milestone | Description | Status |
|---|---|---|
| M1 | | Not started |
| M2 | | Not started |

### Tasks
| ID | Task | Owner | Status |
|---|---|---|---|
| T-001 | | | |

### Rollout Plan
-
-

### Migration Plan
-

### Rollback Plan
-

---

## 9. Testing and Acceptance

### Acceptance Criteria:
- [ ] Given <context, when <action>, then <expected result>.
- [ ]
- [ ]

### Test Scenarios
| Scenario | Expected Result |
|---|---|

### Monitoring/Validation

#### How will we know this works in production?
-

---

## 10. Risks and Open Questions

### Risks
| Risks | Impact | Mitigation |
|---|---|---|

### Open Questsions
| Questsions | Owner | Resolution |
|---|---|---|

---

## 11. Decisions
| Date | Decision | Reason | Owner |
|---|---|---|---|

---

## 12. Change Log
| Version | Date | Author | Summary |
|---|---|---|---|
| 0.1 | | | Initial Draft |

```
    {{< /accordionItem >}}
{{< /accordion >}}

Make it a habit, to keep the **Requirements**, **Decisions**, **Open Questions**, and **Change Log** updated as the spec evolves.

## What we've learned

- What Spec-Driven development is
- What a "Spec" is, and what it could look like
- The difference between Vibe Coding and SDD