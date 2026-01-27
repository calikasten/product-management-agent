---
name: create-jira-ticket
description: Transforms prompts or meeting notes into clear, actionable Jira user stories and bug tickets through structured clarification and explicit acceptance criteria, ready for automated creation via the Atlassian MCP server.
---

# **Purpose**
Creates detailed, actionable Jira user stories and bug tickets suitable for junior developers by asking clarifying questions, structuring requirements with explicit acceptance criteria, and automatically creating tickets via the Atlassian MCP server.

## When To Use
Use this skill when the user wants to create a Jira ticket (user story or bug) from a brief description, meeting notes, or prompt. Do not use this skill for tasks that don't involve Jira ticket creation, or when the user explicitly wants to draft a ticket manually without automated creation.

# **Overall Agent Process**
1. **Receive Initial Prompt:** The user provides a brief description of the task/user story or issue/bug, or references meeting notes containing the task/issue description.
2. **Ask Clarifying Questions:** Ask clarifying questions to gather sufficient details that a junior developer will need to know in order to implement the ticket.
3. **Draft Ticket:** Based on the initial prompt and the user's answers to the clarifying questions, write the user story or bug ticket following the appropriate template.
4. **Create Ticket:** Use the Atlassian MCP server to create the corresponding user story or bug ticket in Jira.

## Specific Process Details
### 1. Receive Initial Prompt
The description of the user story or bug will either be provided initially, or a specific file containing meeting notes with a description of the task/issue will be included in the initial prompt.

### 2. Ask Clarifying Questions
For a user story, the goal of asking clarifying questions is to primarily understand the "what" and "why" of the ticket. For a bug ticket, the goal is to make sure the steps to reproduce the issue are clearly outlined and the desired result is clearly articulated compared to what is currently happening. If any jargon in the initial prompt or ticket description is confusing or unclear, ask clarifying questions.

### 3. Write Ticket Draft
If something in the initial prompt or ticket description relates to specifics on "how" the developer should proceed with implementation, make sure to include that within the acceptance criteria and/or the notes section of the ticket.

If requested to write a user story ticket, the final output should follow this exact user story template:

```markdown
[Short Descriptive Title]
 
**As a** [persona], **I want** [action/outcome], **so that** [reasoning/value].

**Acceptance Criteria:**
GIVEN
WHEN
THEN

[Optional] **Notes:**
- [Bullet point list of important reminders or specifications]
```

If requested to write a bug ticket, the final output should follow this exact bug ticket template:

```markdown
[Short Descriptive Title]

**Summary:** [Description of the problem.]

**Steps to Recreate:**
1. [Numbered step by step instructions for how to reproduce the issue]

**Expected Outcome:**
- [Bullet point(s) of what the intended result is]

**Actual Outcome:**
- [Bullet point(s) of the incorrect behavior that's occurring instead]

[Optional] **Notes:**
- [Bullet point list of important reminders or specifications]
```

### 4. Create Ticket
Create the ticket in the specified Jira project. If a specific epic is stated, link the ticket as a child task to that epic, i.e. the epic should serve as the parent to the newly created ticket.

# **Final Instructions**
1. Make sure to ask the user clarifying questions before writing the ticket.
2. Take the user's answers to the clarifying questions and improve the ticket accordingly.
3. Always use the Atlassian MCP server to create the ticket in Jira after the ticket draft is finalized.
