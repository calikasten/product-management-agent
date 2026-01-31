---
name: executive-update
description: Creates a high-impact status report update for cross-functional executives by synthesizing Jira tickets into strategic outcomes, highlighting customer traction, and framing technical progress as business value.
---
# **Purpose**
Translates technical Jira activity into an executive-ready report that focuses on strategic pillars, customer milestones, and high-level product releases or processes. It prioritizes business outcomes over task completion.

## When To Use
Use this skill when the user requests a status update or progress summary intended for cross-functional partners or executives. Do not use this for internal engineering-only updates or when a granular list of ticket statuses is requested.

# **Overall Agent Process**
1. **Determine Context & Timeframe:** Identify the date range and project.
2. **Retrieve Jira Data:** Fetch issues updated or moved to "Shipped" within the timeframe using the Atlassian MCP server.
3. **Analyze for Strategic Pillars:** Group tickets into business themes based on their impact.
4. **Detect Customer/Brand Updates:** Search ticket summaries and comments for specific brand names or ask the user for recent wins.
5. **Apply Executive Framing:** Translate technical milestones into high-level product releases or foundational processes.
6. **Draft Executive Update:** Write the summary using the specified outcome-focused markdown template.

## Specific Process Details
### 1. Determine Context & Timeframe
Identify the specific date range to analyze. If not provided, default to the last month.

### 3. Analyze for Strategic Pillars
Use best judgment to categorize work items into 3–4 strategic pillars. Common pillars include:
- **Go To Market (GTM) Enablement:** Tools or features that directly support sales, marketing, or customer onboarding.
- **Scaling and Optimization:** Infrastructure improvements, performance gains, or cost-reduction efforts.
- **Quality and Evaluation:** Testing frameworks, model accuracy improvements, or data integrity systems.

### 4. Detect Customer/Brand Updates
Proactively look for brand names in Jira ticket summaries or comments. If found, ensure these are highlighted under a "Customer Traction" pillar. If no customer updates are detected, ask the user: "Were there any customer-specific updates or wins this week to include in the update?"

### 5. Apply Executive Framing
Translate technical milestones into business value. 
- Avoid overly granular technical descriptions (e.g., "Updated scraper logic").
- Use process-oriented value (e.g., "Optimized extraction logic to ensure data accuracy for brand audits").
- Frame technical progress as part of high-level product releases or foundational processes.

### 6. Draft Executive Update
The final output must follow this exact markdown template:

```markdown
[Headline Accomplishment - 1 High-level outcome sentence]

**[Current Month] Accomplishments**
• [Strategic Pillar]: [Outcome-focused milestone or accomplishment]
• [Strategic Pillar]: [Outcome-focused milestone or accomplishment]
• [Strategic Pillar]: [Outcome-focused milestone or accomplishment]

**[Next Month] Focus**
• [Up Next Priority]: [Outcome-focused goal or milestone]
• [Up Next Priority]: [Outcome-focused goal or milestone]
• [Up Next Priority]: [Outcome-focused goal or milestone]
```

# **Final Instructions**
1. Prioritize business outcomes and user value over a list of completed tasks.
2. Ensure all headers for the accomplishments and focus sections use the correct months based on today's date.
3. If brand names are detected, they must be included in a "Customer Traction" or similar strategic pillar.
