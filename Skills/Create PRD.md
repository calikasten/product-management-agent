---
name: create-prd
description: Creates an implementation-ready PRD (Product Requirements Document) by asking structured clarifying questions and organizing validated inputs into a clear, standardized PRD template.
---

# **Purpose**
Creates a detailed, implementation-ready Product Requirements Document (PRD) in Markdown format by asking structured clarifying questions and organizing validated inputs into a clear, standardized template suitable for junior developers.

## When To Use
Use this skill when the user wants to create a PRD for a new feature or functionality. Do not use this skill for tasks that don't involve PRD creation, or when the user explicitly wants to draft requirements in a different format or structure.

# **Overall Agent Process**
1. **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2. **Ask Clarifying Questions:** Before writing the PRD, ask clarifying questions to gather sufficient detail. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out).
3. **Write PRD:** Based on the initial prompt and the user's answers to the clarifying questions, write the PRD.
4. **Save PRD:** Save the generated document as "[PRD - Feature Name].md" and ask the user which directory it should be saved in.

## Specific Process Details
### 1. Receive Initial Prompt
The user provides a brief description or request for a new feature or functionality.

### 2. Ask Clarifying Questions
When asking clarifying questions, format them as a numbered list. This list should support nested sub-questions using dot notation (e.g., 1, 2, 2.1, 2.2, 3). There should only be one atomic question per list item.

Example Format:
1. Top-level question 1?
2. Top-level question 2?
	- 2.1. Sub-question related to question 2?
	- 2.2. Another sub-question related to question 2?
3. Top-level question 3?

Adapt the *actual questions* based on the user's initial prompt, aiming to cover relevant areas like:
- **Goal:** What is the primary goal?
	- **Problem Statement:** What problem does this feature solve? 
	- **Target User:** Who is this feature for?
	- **Success Metrics:** How do we define success for this feature?
- **Core Functionality:** What are the essential actions the user must be able to perform?
	- **Features Summary:** What are must-have features and the user benefits of each one?
	- **(Optional) System Design:** What are key elements that are integral to supporting the core functionality?
	- **(Optional) UI Concepts**: Are there mockups or specific UI preferences?
- **Considerations:** What has not been mentioned that should also be thought about for building this feature?
	- **Scope:** What should this feature explicitly *not* do?
	- **Data:**  What information needs to be displayed or managed?
	- **Edge Cases:** What potential errors or unusual situations should be considered?
	- **(Optional) Dependencies:** What integrations are needed?

### 3. Write PRD
The primary reader is a *junior* developer, so requirements should be explicit, unambiguous, and avoid jargon where possible; make sure to provide enough detail for them to understand the feature's purpose and core logic. Your final output should follow this exact template:
```markdown
# **Overview**
[Brief 2-3 sentence description of what this feature is and why it matters.]
## Problem Statement
[What problem does this feature solve? Why is solving it important now?]
## Goal
[What is the primary goal?]
### Success Metrics
[What are the specific, measurable objectives indicating the feature was successful?]
## Target Users
[Who is this feature for? Be specific about user segments, roles, or personas.]

# **Core Functionality**
## Workflow & Features Summary
[What are the essential actions that must be performed? Break these out into individual sub-features numbered chronologically with H2 feature name. Each individual sub-feature should clearly state the specific functionalities that feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture.")]
## [Optional] Design Considerations
[Layout or design consideration, links to wireframes/mockups, descriptions of relevant components/styles, accessibility requirements, and/or mobile vs desktop differences.]
## [Optional] Non-Functional Requirements
[Description of non-functional requirements to consider for this feature.]

# [Optional] **Considerations**
## Scope
[Manage the scope of this feature by clearly stating what this feature will NOT include.]
## [Optional] Data
[Considerations of what kind of data this feature will require as inputs and what kind of data this feature will produce.]
## [Optional] Edge Cases
[Potential scenarios that "break" the workflow and features defined above and how to handle each instance.]
## Dependencies
[Any known technical constraints, cross-functional or third-party dependencies.]

# **Assumptions & Risks**
## Assumptions
[Hypothesis that must be true in order for this feature to be successful.]
### Risks
[List of risks, their corresponding impact if they occur, and a potential mitigation strategy for each risk.]
```

### 4. Save PRD
- **Format:** markdown (`.md`)
- **Filename:** "[PRD - Feature Name].md" -- e.g., `PRD - User Profile Editing.md`
- **Location:** ask the user which directory to save the file in

# **Final Instructions**
1. Do NOT start implementing the PRD.
2. Make sure to ask the user clarifying questions before writing the PRD.
3. Take the user's answers to the clarifying questions and improve the PRD accordingly.
4. Make sure the PRD output follows the specified document layout/structure.
