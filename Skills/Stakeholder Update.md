---
name: stakeholder-update
description: Creates a concise, business-oriented progress update for senior product stakeholders (e.g., SVP of Product, CPO) by synthesizing recent Jira activity into completed and in-flight work, balancing user/business value with relevant technical detail.
---
# **Purpose**
Translates recent Jira activity into a stakeholder-ready progress update that distinguishes completed work from work still in flight. Each item has a headline and a description that leads with user or business value while including enough technical context for informed stakeholders.

## When To Use
Use this skill when the user requests a progress update or status summary intended for senior product leadership. Do not use for executive-level external communications (use `executive-update`) or engineering-only updates (use `sprint-review-summary`).

# **Overall Agent Process**
1. **Determine Timeframe:** Identify the date range and Jira project to analyze.
2. **Retrieve Jira Data:** Fetch Shipped, QA, and In Progress tickets within the timeframe using the Atlassian MCP server.
3. **Separate Completed from In-Flight:** Group tickets into two buckets — done (Shipped) and in-flight (QA + In Progress).
4. **Group into Milestones:** Within each bucket, combine related tickets into cohesive milestones that tell a single story.
5. **Draft the Update:** Write each milestone as a headline + description block, leading with user or business value and including relevant technical detail.

## Specific Process Details

### 1. Determine Timeframe
Default to the **last 7 days** unless the user specifies otherwise. Ask which Jira project to analyze if the user hasn't specified one. Look up the Cloud ID with `getAccessibleAtlassianResources`.

### 2. Retrieve Jira Data
Use `searchJiraIssuesUsingJql` with `responseContentFormat: markdown`. Fetch up to 50 results. Use three separate queries or a combined JQL query:

```
project = {PROJECT_KEY} AND status in ("Shipped", "QA", "Ready for QA", "In Progress") AND updated >= -7d ORDER BY status ASC
```

Retrieve fields: `summary`, `description`, `status`, `issuetype`, `updated`. Adjust the status names to match the project's workflow if they differ.

### 3. Separate Completed from In-Flight
- **Completed:** Status = Shipped
- **In-Flight:** Status = In Progress, QA, or Ready for QA

The final update must clearly distinguish the two sections. Label them:
- `## Shipped` for completed work
- `## In Progress` for work still in flight (includes both In Progress and QA statuses)

### 4. Group into Milestones
Combine related tickets into a single milestone when they contribute to the same feature, fix, or outcome. A milestone should represent a meaningful deliverable — not an individual ticket. Use judgment: a single high-impact ticket can stand alone; three minor UI tweaks can be grouped.

### 5. Draft the Update
Each milestone follows this format — a bold headline followed by 2–4 bullet points:

```
**[Short Headline]**
- [Why this was prioritized — the user problem, business need, or data quality issue it addresses]
- [What changed or what users can now do]
- [Data or metric if available — e.g., scope of impact, count of items affected, accuracy improvement]
- [Status note for in-flight items: "Currently in QA" or "In development"]
```

**Tone guidance:**
- Write for senior product leaders who understand the product and care about *why* work was prioritized, not just *what* shipped.
- The first bullet should always answer "why did this matter?" — frame it as a user problem solved, a business risk addressed, or a data quality gap closed.
- Include a metric or data point when one exists in the ticket (e.g., number of items affected, percentage, count of customers impacted). If no metric exists, describe the concrete outcome.
- Keep bullets tight — one idea per bullet, no full paragraphs.
- For in-flight items, the last bullet should note current status.

**Example milestone (Shipped):**
```
**Account Eligibility — Accurate Data Across the App**
- Customers were being shown metrics for features they weren't eligible for, making their dashboards misleading.
- All metrics, tables, and modules now filter to only the features an account is eligible for, powered by a new eligibility table.
- The app also now hides modules with no approved content, giving the team manual control over what appears per account.
```

**Example milestone (In Progress):**
```
**Catalog Toolbar — Filter, Sort, and Search Controls**
- Users have no way to quickly find or narrow items in the catalog today, which slows down content review workflows.
- Building four new toolbar interactions: filter chips, a sort dropdown, free text search, and dynamic chip filtering.
- Currently in development; targeting QA this sprint.
```

# **Final Instructions**
1. Always produce two clearly labeled sections: **Shipped** and **In Progress**. If one section has no tickets, include it with a note: "Nothing shipped this period." or "No work currently in flight."
2. The first bullet of every milestone must answer "why did this matter?" — never open with what was built.
3. Include a metric or data point in at least one bullet per milestone when the ticket provides one. If none exists, describe the concrete outcome or scope.
4. Keep bullets tight — one idea each, no full paragraphs inside bullets.
5. Do not list individual ticket keys in the output unless they add meaningful context.
6. If no tickets are returned for the timeframe, tell the user and ask whether to expand the date range.
