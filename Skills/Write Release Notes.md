
---
name: write-release-notes
description: Creates clear, non-technical release notes by analyzing shipped Jira tickets and translating recent features and fixes into concise explanations of workflow changes and user benefits.
---

# **Purpose**
Creates clear, non-technical release notes by analyzing shipped Jira tickets and translating recent features and fixes into concise explanations of workflow changes and user benefits.

## When To Use
Use this skill when the user wants to create release notes based on shipped Jira tickets. Do not use this skill for tasks that don't involve creating release notes, or when the user wants to document tickets in a different format or structure.

# **Overall Agent Process**
1. **Determine Relevant Timeframe:** If not provided in the initial prompt, ask the user for the date range to analyze tickets for; e.g.: if writing release notes for tickets shipped this week, the timeframe is today -7.
2. **Filter Jira Tickets to Timeframe:** Filter the tickets in the Jira project to only those that moved into the "shipped" status in the relevant timeframe.
3. **Analyze Tickets:** Review each ticket to understand the feature/functionality and the corresponding user impact.
4. **Write Release Notes:** Compile the findings and analysis into clear and concise release notes.
5. **Save Release Notes:** Save the generated document as "PRD - [Feature Name].md" and ask the user which directory it should be saved in.

## Specific Process Details
### 1. Determine Relevant Timeframe
If not provided in the initial prompt, ask the user for the date range to analyze tickets for; e.g.: if writing release notes for tickets shipped this week, the timeframe is today -7.

### 2. Filter Jira Tickets to Timeframe
Filter the tickets in the Jira project to only those that moved into the "shipped" status in the relevant timeframe.

### 3. Analyze Tickets
Review each ticket to understand the feature/functionality and the corresponding user impact. Focus on identifying:
- New user-facing features and functionality
- Bugs that were negatively impacting user experience
- Changes to user workflows
- User benefits from the shipped tickets

### 4. Write Release Notes
Write release notes geared towards a non-technical user that describes everything that has been released ("shipped") for the Jira project in the specified timeframe. Start the release notes with a one sentence, high-level summary of the user benefits addressed in the released tickets. Group related tickets into the overarching features/functionality. Use bullet points under each feature to describe the issue or problem the user was previously encountering and how the shipped tickets remedy this. Include a summary of the changes, especially around updates to user workflows and describing the impact of the changes for user experience. The final output should follow this exact template:

```markdown
**[date] Release Notes**

[High-level summary of user benefits released to production.]

**[Name of Feature 1]**
- [Bullet point of previous issue]
- [Bullet point describing changes made to workflow]
- [Bullet point summarizing new user benefits from feature/functionality]

**[Name of Feature 2]**
- [Bullet point of previous issue]
- [Bullet point describing changes made to workflow]
- [Bullet point summarizing new user benefits from feature/functionality]

**[Name of Feature 3]**
- [Bullet point of previous issue]
- [Bullet point describing changes made to workflow]
- [Bullet point summarizing new user benefits from feature/functionality]
```

# **Final Instructions**
1. Ask clarifying questions if context is missing, such as the specific timeframe or which Jira project to analyze.
2. Focus on user-facing changes and benefits rather than technical implementation details.
3. Group related tickets into cohesive features or functionality.
4. Write in clear, non-technical language that users can easily understand.
