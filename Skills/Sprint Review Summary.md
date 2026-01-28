---
name: sprint-review-summary
description: Creates a status report update that summarizes development team progress by analyzing Jira tickets to highlight shipped work, blockers, in-progress items, and upcoming priorities for a specified timeframe.
---
# **Purpose**
Creates a status report update that summarizes development team progress by analyzing Jira tickets to highlight shipped work, blockers, in-progress items, and upcoming priorities for a specified timeframe.

## When To Use
Use this skill when the user wants to create a sprint review summary or weekly status report based on Jira tickets. Do not use this skill for tasks that don't involve analyzing Jira tickets or creating status reports, or when the user wants a different format or analysis approach.

# **Overall Agent Process**
1. **Determine Relevant Timeframe:** Identify the date range to analyze tickets for; e.g.: if reviewing the past week's progress, the timeframe is today -7.
2. **Filter Jira Tickets to Timeframe:** Filter the tickets in the specified Jira project to only those updated in the relevant timeframe.
3. **Determine Ticket Statuses:** Review the status of each ticket updated to understand what was completed ("shipped"), what is in progress ("in progress"/"testing/code review"), and what is up next ("ready for development").
4. **Analyze Ticket Comments:** Review comments from each ticket to understand if there is any additional context relevant to that ticket like a blocker description, dependency, or reminders.
5. **Write Summary Report:** Compile the findings and analysis into a summary report of development team progress for the timeframe.

## Specific Process Details
### 1. Determine Relevant Timeframe
Identify the date range to analyze tickets for; e.g.: if reviewing the past week's progress, the timeframe is today -7.

### 2. Filter Jira Tickets to Timeframe
Filter the tickets in the specified Jira project to only those updated in the relevant timeframe.

### 3. Determine Ticket Statuses
Review the status of each ticket updated to understand what was completed ("shipped"), what is in progress ("in progress"/"testing/code review"), and what is up next ("ready for development").

### 4. Analyze Ticket Comments
Review comments from each ticket to understand if there is any additional context relevant to that ticket like a blocker description, dependency, or reminders.

### 5. Write Summary Report
Write a status report update geared towards executive cross-functional partners that describes everything that has happened in the last week for the Jira project. Add notes where relevant with additional context, especially around describing the impact of each work item for users and user experience. Call out if there are any comments indicating delays or blockers for specific work items. Start the status report update with a one sentence summary of the progress this week. Use bullet points for each work item and list the items based on their summary/ticket title and hyperlink that text to the exact Jira ticket. The final output should follow this exact template:

```markdown
**Summary:** [1-2 sentence high-level summary of progress for this week.]

**Shipped:**
- Ticket 1 - additional ticket context stating user or business value
- Ticket 2 - additional ticket context stating user or business value

**Blockers:**
- Ticket 3 - additional ticket context explaining the blocker
- Ticket 4 - additional ticket context explaining the blocker
  
**In Progress:**
- Ticket 5 - additional ticket context stating user or business value
- Ticket 6 - additional ticket context stating user or business value
- Ticket 7 - additional ticket context stating user or business value

**Up Next:**
- Ticket 8 - additional ticket context stating user or business value
- Ticket 9 - additional ticket context stating user or business value
```

# **Final Instructions**
1. Ask clarifying questions if context is missing, such as the specific timeframe to analyze or which Jira project to review.
2. Ensure all ticket titles are hyperlinked to their corresponding Jira tickets.
3. Focus on user and business value when describing work items.
4. Clearly call out any blockers or delays mentioned in ticket comments.
