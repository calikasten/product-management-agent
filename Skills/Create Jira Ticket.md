---
name: create-jira-ticket
description: Transforms prompts or meeting notes into clear, actionable Jira tickets (Stories, Bugs, Spikes, Chores) through structured clarification and explicit acceptance criteria, ready for automated creation via the Atlassian MCP server.
---

# **Purpose**
Creates detailed, actionable Jira tickets suitable for development teams by asking clarifying questions, categorizing work into specific types (user stories, bugs, research spikes, tasks/chores), and ensuring requirements follow industry standards like INVEST and Gherkin syntax.

## When To Use
Use this skill when the user wants to a create Jira ticket from a brief description, meeting notes, or prompt. Do not use this skill for tasks that don't involve Jira ticket creation.

# **Overall Agent Process**
1. **Identify Work Type:** Determine if the request is for a user story, bug, research spike, or task/chore.
2. **Ask Clarifying Questions:** Gather sufficient details for the specific work type to ensure a "definition of done" can be established.
3. **Draft Ticket:** Format the ticket using the appropriate template and principles (INVEST for stories, reproduction steps for bugs, etc.).
4. **Create Ticket:** Use the Atlassian MCP server to create the ticket in Jira.

## Specific Process Details

### 1. Identify Work Type
- **User Story:** New functionality from a user's perspective.
- **Bug:** Fixing something that is broken (unexpected behavior).
- **Spike:** Research, architecture, or refactoring to answer a question or prepare for future work.
- **Chore:** "Invisible" work providing value to the team (maintenance, setup, etc.).

### 2. Ask Clarifying Questions
- **For Stories:** Focus on the "what" and "why". Avoid "how" (implementation details). Ensure the story is Independent, Negotiable, Valuable, Estimable, Small, and Testable (INVEST).
    - **I**ndependent: Can stand alone regardless of implementation order.
    - **N**egotiable: General enough for developers to collaborate on implementation.
    - **V**aluable: Delivers something the user cares about.
    - **E**stimate-able: Possible to evaluate the size/effort.
    - **S**mall: The smallest possible unit of work that can be completed in a single sprint. Small stories provide frequent value and visibility into progress. Proactively suggest "splitting" a story if it appears too large or complex.
    - **T**estable: Enough information exists to verify the story is done.
- **For Bugs:** Ensure steps to recreate are precise. Identify the impact and severity.
- **For Spikes:** Ask for the specific question to be answered, the background, and the desired timebox.
- **For Chores:** Understand the value to the team and the specific tasks involved.

### 3. Draft Ticket
Use the following templates for the identified work type:

#### **User Story (New Functionality)**
Stories must follow the INVEST acronym. Use Gherkin syntax for Acceptance Criteria.

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

#### **Fixing Something (Bug)**
Bugs do not undergo estimation and should focus on reproduction.

```markdown
[Short Descriptive Title]

**Summary:** [Description of the problem, impact, and severity.]

**Steps to Recreate:**
1. [Step 1]
2. [Step 2]

**Expected Outcome:**
- [The intended result]

**Actual Outcome:**
- [The incorrect behavior occurring instead]

[Optional] **Notes:**
- [Device, browser, or environment details]
```

#### **Research (Spike)**
Spikes are timeboxed and focus on exploration rather than implementation.

```markdown
[Short Descriptive Title] - Spike

**Background:** [Context and why this research is necessary.]

**Timebox:** [Duration, e.g., 4 hours, 1 day]

**Goal:** [What must be accomplished/answered to consider this done?]

[Optional] **Notes:**
- [Links to documentation or related research]
```

#### **Task (Chore)**
Miscellaneous work for the product team.

```markdown
[Short Descriptive Title]

**Description:** [What needs to be done and why it's valuable to the team.]

**Tasks:**
- [Specific checklist of items]

[Optional] **Notes:**
- [Any technical constraints]
```

### 4. Create Ticket
- Project: Ask user to specify which project to create the ticket in.
- Link to an Epic as a child task if an Epic is mentioned.

# **Final Instructions**
1. **Validate against INVEST:** Before finalizing a User Story, ensure it is Small enough for one sprint and Testable.
2. **Story Splitting:** If a user story covers multiple outcomes or seems too large for a single sprint, proactively suggest "splitting" it into multiple smaller, more focused stories.
3. **Gherkin Syntax:** Always use GIVEN/WHEN/THEN for User Story acceptance criteria to ensure a clear "definition of done."
4. **Avoid Implementation in User Stories:** Ensure User Stories focus on *what* and *why*. If implementation details (the *how*) are provided, move them to the "Notes" section instead of the Story description.
4. **Timebox Spikes:** Never leave a Spike open-ended; always include a suggested or requested timebox.
5. **Automate:** Use the Atlassian MCP tool to create the ticket after the draft is approved.
