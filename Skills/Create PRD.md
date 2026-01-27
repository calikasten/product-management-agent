---
name: create-prd
description: Creates an implementation-ready PRD (Product Requirements Document) by asking structured clarifying questions and organizing validated inputs into a clear, standardized PRD template.
---

# **Purpose**
Creates a detailed, implementation-ready PRD (Product Requirements Document ) to align goals, outcomes, and requirements. It serves as the initial proposal to guide discovery, structure development efforts, and define the MVP critical path.

## When To Use
Use this skill when the user wants to create a PRD for a new product, feature, or functionality. It is especially useful for complex projects requiring alignment across business, user, and technical perspectives.

# **Overall Agent Process**
1. **Ask Clarifying Questions:** Gather details across the five requirement types (Business, Functional, User, Technical, Non-functional) and identify the core problem/root cause.
2. **Write PRD:** Organize inputs into the standardized template, including gap analysis and MVP definition.
3. **Save PRD:** Save as "PRD - [Feature Name].md" in the user's specified directory.

## Specific Process Details

### 1. Ask Clarifying Questions
Structure questions as a numbered list with nested sub-questions (e.g., 1, 2, 2.1). Cover:
- **Problem & Root Cause:** Why is this important? Who is impacted? What is the root cause?
- **Gap Analysis:** What is the current state? What is the desired state?
- **Target Audience:** Market assessment and target demographics.
- **Requirement Types:**
    - *Business:* Why is the product needed?
    - *Functional:* What should the product do?
    - *User:* Tasks the user can perform.
    - *Technical:* Security, network, platform, or integration needs.
    - *Non-functional:* Performance, reliability, scalability (Sprint 0 concerns).
- **Success & Evaluation:** How will we measure if the solution was beneficial?

### 2. Write PRD Template
The final output must follow the exact structure of this template:

```markdown
# **Overview**
[Brief 2-3 sentence description of what this feature/product is and why it matters.]

## Problem Statement & Root Cause
[What problem does this feature solve? Why is solving it important now? What is the root cause?]

## Goal
[What is the primary goal? How does it align with business requirements?]

### Success Metrics & Evaluation Plan
[What are the specific, measurable objectives? How will we measure if the solution was beneficial?]

## Target Users & Market Assessment
[Who is this feature for? Include user segments, roles, or personas and target demographics.]

## Gap Analysis
### Current State
[Description of the existing problem or how things work today.]
### Desired State
[The vision for how things should work once implemented.]
### The Gap
[The specific delta between current and desired states.]

# **Core Functionality**
## Workflow & Features Summary
[Break these out into individual sub-features numbered chronologically as ## Feature Name. Include both User Requirements (tasks) and Functional Requirements (behaviors). Each individual sub-feature should clearly state the specific functionalities that feature must have.]

# **MVP & Implementation Considerations**
## Critical Path & MVP Definition
[Identify the coherent list of what needs to be done to deliver the MVP as the first releasable instance for user feedback.]

## Scope
[Clearly state what this feature will NOT include.]

## [Optional] Design Considerations
[Layout, wireframes/mockups, descriptions of relevant components/styles, accessibility requirements, and/or operational logistics like workflows or process maps.]

## [Optional] Technical & Non-Functional Requirements
[Security, network, platform, or integrations. Include Sprint 0 concerns like performance, reliability, maintainability, scalability, or usability.]

## [Optional] Data
[Considerations of what kind of data this feature will require as inputs and what kind of data this feature will produce.]

# **Assumptions & Risks**
## Assumptions
[Hypothesis that must be true in order for this feature to be successful.]

## [Optional] Edge Cases & Dependencies
[Potential scenarios that "break" the workflow and how to handle them. Include any known technical constraints or third-party dependencies.]

## Risks
[List of risks, impact, and mitigation strategies.]
```

### 3. Save PRD
- **Format:** markdown (`.md`)
- **Filename:** `PRD - [Feature Name].md`
- **Location:** Ask the user which directory to save the file in.

# **Final Instructions**
1. **Focus on the "Why" and "What":** Communicate the value and behaviors needed, leaving the "how" for design/system blueprints.
2. **Prioritize the MVP:** Clearly distinguish between the critical path for the MVP and future iterations.
3. **Address the Gap:** Ensure the transition from Current State to Desired State is logical and fully addressed by the requirements.
4. **Sprint 0 Thinking:** Include explicit non-functional requirements to inform the system's architecture and constraints.
