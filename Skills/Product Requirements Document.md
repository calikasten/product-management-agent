---
name: product-requirements-document
description: Creates an implementation-ready PRD (Product Requirements Document) by asking structured clarifying questions and organizing validated inputs into a clear, standardized PRD template.
---

# **Purpose**
Creates a detailed, implementation-ready PRD that aligns goals, outcomes, and requirements while staying concise and scannable for Product, Design, and Engineering. It serves as the initial proposal to guide discovery, structure development efforts, and define the MVP critical path.

## When To Use
Use this skill when the user wants to create, rewrite, expand, or clean up a PRD for a new product, feature, or functionality. It is especially useful for complex projects that require alignment across business, user, and technical perspectives. Do not use this skill for Jira ticket creation, release notes, or executive updates unless the user explicitly asks for PRD output.

# **Overall Agent Process**
1. **Confirm Context:** Identify the initiative, audience, and whether the PRD is net-new or a revision.
2. **Ask Structured Clarifying Questions:** Gather details across the five requirement types (Business, Functional, User, Technical, Non-functional), plus problem/root cause and success evaluation.
3. **Capture Core Inputs:** Organize the problem, gap analysis, goal, users, workflow, features, dependencies, risks, and MVP critical path.
4. **Draft in House Style:** Write the PRD using the required section order, header hierarchy, and bullet patterns.
5. **Refine for Clarity:** Remove fluff, tighten language, and ensure every section is specific and actionable.
6. **Validate Completeness:** Confirm scope boundaries, assumptions, dependencies, and acceptance criteria are clear and testable.
7. **Save PRD:** Save the final PRD as `PRD - [Feature Name].md` in the user-specified directory.

## Specific Process Details
### 1. Confirm Context
If critical context is missing, ask focused clarifying questions before drafting:
- What initiative or feature does this PRD cover?
- Who is the primary audience and decision-maker?
- Is this net-new or a revision of an existing PRD?
- What timeline, constraints, or dependencies matter most?

### 2. Ask Structured Clarifying Questions
Ask questions as a numbered list with nested sub-questions when needed (for example: 1, 2, 2.1). Cover:
- Problem and root cause:
  - Why is this important now?
  - Who is impacted?
  - What is the root cause?
- Gap analysis:
  - What is the current state?
  - What is the desired state?
  - What is the specific gap between the two?
- Target users and market context:
  - Who is this for?
  - What user segments, roles, or demographics matter most?
- Requirement types:
  - Business requirements (why the product/feature is needed)
  - Functional requirements (what behaviors the system must support)
  - User requirements (what tasks users must be able to perform)
  - Technical requirements (security, platform, network, integrations)
  - Non-functional requirements (performance, reliability, scalability, maintainability, usability)
- Success and evaluation:
  - How will we measure whether the solution is beneficial?

### 3. Capture Core Inputs
Collect and organize the minimum inputs needed for a strong PRD:
- Problem statement grounded in user and business impact
- Root cause framing
- Gap analysis (Current State, Desired State, The Gap)
- Goal and intended outcomes
- Target user definition
- End-to-end user workflow
- Feature-level requirements
- Input dependencies, data sources, and systems
- Assumptions and risks
- MVP critical path definition
- Scope exclusions and non-goals

### 4. Draft in House Style
Use this structure by default unless the user explicitly asks for a different template:

```
# Overview
## Problem Statement
## Goal
### Success Metrics
## Target Users
# Core Functionality
## User Journey/Workflow
### Feature 1: ... (repeat for each feature)
# Considerations
## Scope
```

Formatting and tone requirements:
- Use concise, direct prose with short paragraphs.
- Use numbered lists for sequential workflows.
- Use bullet points for capabilities, details, and inputs.
- Use bolded subsection labels within feature sections, for example:
  - `**Front-End Screen:**`
  - `**Back-End Workflow:**`
  - `**Inputs:**`
- Keep language concrete and operational; avoid filler and vague claims.
- Focus on the "why" and the "what"; avoid over-specifying the implementation "how."

### 5. Refine for Clarity
Pressure-test each section before finalizing:
- Does the problem clearly explain why now and why it matters?
- Is the root cause explicit and evidence-based?
- Does the gap analysis clearly connect current state to desired state?
- Are goals measurable and tied to outcomes?
- Are workflows readable from end to end without ambiguity?
- Are feature details specific enough for Design and Engineering planning?
- Are dependencies and input sources explicit?

### 6. Validate Completeness
Before delivering the PRD:
- Confirm sections are complete and in the right order.
- Ensure scope explicitly lists non-goals.
- Ensure acceptance criteria, when included, use GIVEN/WHEN/THEN syntax.
- Flag assumptions, open questions, and unresolved decisions.
- Include non-functional requirements where they materially affect architecture or delivery planning.

### 7. Save PRD
- Format: markdown (`.md`)
- Filename: `PRD - [Feature Name].md`
- Location: ask the user which directory to save the file in.

# **Final Instructions**
1. Default to the house PRD format and style from `agentic-discovery/PRD - Content Readiness.md`.
2. Preserve the user's domain language: Foundry is a platform; Agentic Discovery is a solution.
3. Follow all relevant writing guidance from `effective-writer` (clarity, precision, direct voice, and editing rigor) unless it conflicts with PRD structure requirements in this skill.
4. Prioritize PRD succinctness and skimmability from this skill over broader writing preferences when there is any conflict.
5. Keep output high-signal with clear headers and bullet discipline.
6. Prioritize the MVP by explicitly distinguishing critical path requirements from future iterations.
7. Ensure the transition from Current State to Desired State is logically addressed by requirements.
8. Ask clarifying questions only when missing context would materially reduce PRD quality.
