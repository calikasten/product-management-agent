---
name: split-user-stories
description: Splits large or complex user stories into smaller, high-value units of work to reduce risk, increase visibility, and maintain a steady delivery cadence.
---

# **Purpose**
This skill helps product managers and development teams decompose large or complex user stories into the smallest possible units of value. By applying structured logic or technical decomposition, it ensures stories are manageable, estimable, and ready for a single sprint.

## When To Use
- Use when a user story contains conjunctions ("and", "or", "but").
- Use when a story involves multiple user personas or roles.
- Use when the development team struggles to estimate a story or gives highly variable estimates.
- Use when a story is expected to take more than one sprint.
- Use when value can be realized earlier through a smaller increment.
- **Do not use** for bugs, research spikes, or simple chores unless they can be logically broken down into independent value-adds.

# **Overall Agent Process**
1. **Analyze the Story:** Review the original story for complexity indicators (conjunctions, multiple roles, broad scope).
2. **Diagnose Splitting Method:** Determine if the story is better suited for "Splitting Case Logic" (outcome-oriented) or the "Hamburger Method" (technical/quality-oriented).
3. **Apply 1+N Pattern:** If the story involves repetitive updates (e.g., "update 5 pages"), split into "1 proof-of-concept" and "N remaining items" to reduce risk.
4. **Split Automatically:** Generate the smaller stories using the standard template.
5. **Review Against INVEST:** Ensure each split story is Independent, Negotiable, Valuable, Estimable, Small, and Testable.

## Specific Process Details

### 2. Diagnose Splitting Method
- **Splitting Case Logic:** Use this for stories that have clear workflow steps, business rule variations, or data variations.
- **Hamburger Method:** Use this when a team is stuck on technical implementation or cannot see how to deliver value vertically. Identify technical layers (DB, API, UI) and "bite" through them at different quality levels (e.g., Manual -> Automated -> Optimized).

### 3. Apply 1+N Pattern
For any story involving repetitive actions across multiple entities:
- **Story 1:** Implement the change for a single representative entity (the "1"). This reduces risk and establishes the pattern.
- **Story 2:** Implement the change for the remaining "N" entities following the established pattern.

### 4. Split Automatically
Each split story must follow the `create-jira-ticket` format:

```markdown
[Short Descriptive Title]

**As a** [persona], **I want** [action/outcome] **so that** [reasoning/value].

**Acceptance Criteria:**
GIVEN [condition/context]
WHEN [trigger/action]
THEN [expected result/value]

[Optional] **Notes:**
- [Important reminders or technical specifications]
```

# **Final Instructions**
1. **Remove Conjunctions:** Ensure "and", "or", and "but" are removed from the "I want" and "so that" sections of split stories.
2. **Verify Value:** Every split story must deliver a demonstrable increment of value to a persona. Avoid purely "technical" splits (e.g., "Create Database Table") that provide no user-facing utility.
3. **Risk Reduction:** Prioritize splits that allow the team to learn or fail fast on the most complex part of the original story.
4. **Automate Output:** Present the final list of split stories clearly, ready for review or ticket creation.

