---
name: executive-update
description: Creates a high-impact status report update for cross-functional executives by synthesizing Jira tickets into strategic outcomes, highlighting customer traction, and framing technical progress as business value.
---
# **Purpose**
Translates technical Jira activity into an executive-ready report using a standardized milestone format. Each milestone includes a headline, description, key metric or proof point, and audience. Prioritizes business outcomes and concrete evidence over task lists.

## When To Use
Use this skill when the user requests a status update or progress summary intended for cross-functional partners or executives. Do not use this for internal engineering-only updates or when a granular list of ticket statuses is requested.

# **Overall Agent Process**
1. **Determine Context & Timeframe:** Identify the date range and project.
2. **Retrieve Jira Data:** Fetch issues updated or moved to "Shipped" within the timeframe using the Atlassian MCP server.
3. **Analyze for Milestones:** Group related tickets into cohesive milestones based on business impact.
4. **Detect Customer/Brand Updates:** Search ticket summaries and comments for specific brand names or ask the user for recent wins.
5. **Apply Executive Framing:** Translate each milestone into a concise headline, description, and proof point.
6. **Draft Executive Update:** Write the summary using the specified milestone format.

## Specific Process Details
### 1. Determine Context & Timeframe
Identify the specific date range to analyze. If not provided, default to the last month. Ask which Jira project to analyze if the user hasn't specified one.

### 2. Retrieve Jira Data
Use `searchJiraIssuesUsingJql` with `responseContentFormat: markdown`, fetching up to 100 results (paginate if more). Pull tickets that moved to "Shipped" or were updated within the timeframe, and retrieve `summary`, `description`, `status`, `issuetype`, `parent`, and `comment`. Fetch parent epics when child tickets alone don't explain the business value.

### 3. Analyze for Milestones
Group related tickets into coherent milestones. Each milestone should represent a meaningful deliverable—a completed feature, process improvement, or infrastructure change. Combine related tickets when they tell a single story. Include **no more than 4 milestones**—pick the strongest rather than listing everything.

### 4. Detect Customer/Brand Updates
Proactively look for brand names in Jira ticket summaries or comments. If found, include them as milestones or within milestone descriptions. If no customer updates are detected, ask the user: "Were there any customer-specific updates or wins this week to include in the update?"

### 5. Apply Executive Framing
For each milestone:
- **Milestone Headline:** Short, descriptive title (e.g., "Automated URL Retrieval Process"). Avoid jargon.
- **Milestone Description:** 2–3 sentences explaining what was done, why it matters, and context (e.g., prerequisites, downstream impact). Use process-oriented language. Avoid overly granular technical details.
- **Key Metric / Proof Point:** Quantitative or qualitative evidence—numbers, percentages, specific outcomes (e.g., "92.90% automated URL coverage"). If no metric exists, describe the concrete outcome or capability delivered.
- **Audience:** Default to "Internal" unless the milestone is customer-facing or external.

### 6. Draft Executive Update
The final output must follow this exact format. Each milestone is a block; separate blocks with a blank line:

```markdown
Milestone Headline: [Short descriptive title]
Milestone Description: [2–3 sentences: what was done, why it matters, context. Process-oriented, avoid jargon.]
Key Metric / Proof Point: [Numbers, percentages, or concrete outcome. E.g., "676 products tested: 92.90% automated URL coverage."]
Audience: Internal

Milestone Headline: [Next milestone title]
Milestone Description: [Description]
Key Metric / Proof Point: [Proof point]
Audience: Internal
```

# **Final Instructions**
1. Apply relevant writing guidance from `effective-writer` for clarity, structure, and editing rigor.
2. Each milestone must include all four fields: Milestone Headline, Milestone Description, Key Metric / Proof Point, Audience.
3. Prioritize business outcomes and user value over a list of completed tasks.
4. Include specific numbers and percentages when available in tickets; otherwise describe the concrete capability or outcome.
5. If brand names are detected, incorporate them into milestone descriptions or create a dedicated customer traction milestone.
6. Include no more than 4 milestones. Choose the strongest by business impact rather than listing everything.
