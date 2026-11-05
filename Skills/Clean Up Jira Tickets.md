---
name: cleanup-jira-tickets
description: Audits Jira tickets in a given project for a given time range, identifies formatting violations, drafts corrected versions, and pushes approved fixes to Jira — including descriptions, title casing, spike title format, and reporter assignment.
---

# **Purpose**
Audits Jira tickets against formatting standards for Stories, Bugs, Spikes, and Chores, then fixes non-compliant tickets in bulk via the Atlassian MCP server.

## When To Use
Use this skill when the user wants to review and clean up recently created Jira tickets for formatting compliance. Do not use for creating new tickets (use `create-jira-ticket` instead) or for updating ticket content beyond formatting.

# **Overall Agent Process**
1. **Fetch Tickets:** Query Jira for tickets in the target project and time range.
2. **Audit Each Ticket:** Evaluate every ticket against the format rules for its issue type.
3. **Report Violations:** Present a clear summary of which tickets are non-compliant and why.
4. **Draft Fixes:** Write corrected descriptions and summaries for all non-compliant tickets.
5. **Get Approval:** Present all drafts to the user before making any changes.
6. **Push Updates:** On approval, push all fixes to Jira in parallel via the Atlassian MCP server.
7. **Add Attribution Comments:** For each ticket updated, add a comment noting that it was re-worded by Claude.

## Specific Process Details

### 1. Fetch Tickets

**Defaults (use unless the user specifies otherwise):**
- Project: ask the user which Jira project to audit if they haven't specified one.
- Time range: **past 7 days** (`created >= -7d`)
- Cloud ID: look it up with `getAccessibleAtlassianResources`.

Use `searchJiraIssuesUsingJql` with fields: `summary`, `description`, `issuetype`, `status`, `assignee`, `reporter`, `created`. Request up to 50 results. Use `responseContentFormat: markdown`.

### 2. Audit Each Ticket

For each ticket, check the following based on its Jira issue type:

#### Story (issue type: "Story")
The description must contain all of the following:
- `**As a**` ... `**I want**` ... `**so that**` — one-line user story statement
- **Approved persona** in the `**As a**` clause — it must be exactly one of: **Foundry engineer**, **Foundry PM**, or **Agentic Discovery app user**. Flag any other persona (e.g. "Foundry operator", "Foundry data engineer", "signal author", "product owner", "brand user in Foundry", a brand name). Map to the closest approved persona from the ticket's content (backend/data pipeline/infrastructure → Foundry engineer; internal tooling, process, or PM-run skills/DAGs → Foundry PM; dashboard or brand-facing app features → Agentic Discovery app user). **If the right persona isn't clear from the ticket, don't guess — ask the user which one to use** before drafting that ticket.
- Acceptance criteria header — either `**Acceptance Criteria:**` **or** incrementally numbered blocks. Both formats are compliant. For numbered blocks, the entire label plus description must be bolded as one unit — `**AC #1: <description>**` — not just the `AC #1:` label with a plain-text description after it.
- `GIVEN` / `WHEN` / `THEN` — all caps, no bullets, each on its own line separated by a hard return/carriage return (an actual line break, not just wrapped text within one paragraph)

Flag if any of these are missing or if the description is empty. Also flag GIVEN/WHEN/THEN clauses that are present but run together without a hard return between them (e.g. merged into one line or one paragraph).

**Line spacing in numbered AC blocks:** The AC title and its GIVEN / WHEN / THEN (and AND) lines are stacked with single hard returns only — no blank lines between the AC title and `GIVEN`, or between `GIVEN`, `WHEN`, `THEN`, and `AND`. Use a blank line only to separate one AC block from the next. These should be soft returns (Shift+Enter in Jira), not separate paragraphs.

**Tooling limitation:** The Jira update tool converts every line break in a markdown description into a separate paragraph, so it cannot produce soft returns. Trailing spaces, single newlines, backslash line endings, and ADF input all fail, and sending HTML (`<br>`) rewrites the whole ticket as HTML — do not use it. So when a numbered AC block has blank lines between its lines, flag it in the report and tell the user it needs a manual Shift+Enter fix in Jira. Do not re-push those descriptions, and never overwrite a description that already has soft returns, since the push would replace them with paragraphs.

Wrap identifiers containing underscores or braces in backticks, and avoid braces inside code spans (the converter mangles them).

#### Bug (issue type: "Bug")
The description must contain:
- `**Summary:**` — description of the problem and impact
- `**Steps to Recreate:**` — numbered list
- `**Expected Outcome:**`
- `**Actual Outcome:**`

Also flag tickets typed as "Story" whose title or description clearly describes a defect (unexpected behavior, something "matching when it shouldn't", "returning wrong value", etc.) — these should be noted as candidates for issue type change to Bug.

#### Spike (issue type: "Story" or "Task" with "SPIKE" in the title)
The description must contain:
- `**Background:**`
- `**Timebox:**`
- `**Goal:**`

The summary must begin with `SPIKE -- ` (two dashes, space after).

#### Chore / Task (issue type: "Task")
The description must contain:
- `**Description:**`
- `**Tasks:**` — checklist of items

#### All Ticket Types
- **Title casing:** Summary must be in title case. Lowercase: prepositions (`in`, `on`, `for`, `from`, `to`, `of`, `at`, `via`, `with`), articles (`a`, `an`, `the`), and short conjunctions (`and`, `but`, `or`, `nor`). Exception: always capitalize the first word.
- **Reporter:** Should be set to Cali Kasten. Flag if not set to her.
- **Team member names:** Do not include role qualifiers. Use the person's name only (e.g., "Alex", not "Alex (SVP)").
- **Environment names:** Any reference to an environment must state **DEV** or **PROD**, always in all caps (not "dev", "Dev", "prod", "Prod", or "production"). Flag lowercase or mixed-case mentions, and flag tickets where an environment is implied but not stated. Don't change `dev`/`prod` inside code identifiers, paths, or table names (e.g., a `prod` schema); only the prose. If the intended environment isn't clear from the ticket, ask the user.

### 3. Report Violations

Present a table or list showing:
- Ticket key + linked summary
- Issue type
- What's wrong (e.g., "Empty description", "Missing GIVEN/WHEN/THEN", "Title not title case", "Spike missing Timebox", "Non-approved persona")

Clearly separate tickets that are **fully compliant** from those that **need fixes**.

### 4. Draft Fixes

For each non-compliant ticket, draft:
1. A corrected **summary** (proper title case; spike prefix if applicable)
2. A corrected **description** using the appropriate template

**Personas:** Every story must use one of the approved personas below, whether the description is sparse or fully written. Replace non-approved personas when drafting fixes, and ask the user when the correct one can't be determined from the ticket.

**When drafting from sparse context (e.g., empty description):** Infer intent from the title. Use the correct persona defaults:
- **Foundry engineer** — for backend, data pipeline, or infrastructure work
- **Foundry PM** — for internal tooling or process stories
- **Agentic Discovery app user** — for dashboard or brand-facing features

**Voice:** PM-to-eng tone. Short clauses. `**I want**` = tight hook. `**so that**` = one plain-language benefit. One GIVEN/WHEN/THEN for the main behavior; edge cases go in Notes.

**Do not** include team member role qualifiers (e.g., write "Alex", not "Alex (SVP)").

**For issue type mismatches** (e.g., a Bug filed as a Story): Draft the description in the correct format and note the suggested issue type change. Warn the user that issue type cannot be changed via the API and must be updated manually in Jira.

### 5. Get Approval

Present all drafts grouped by ticket. Ask the user to confirm before pushing. Allow the user to:
- Approve all at once
- Approve specific tickets
- Skip a ticket
- Request changes to a draft before pushing

### 6. Push Updates

For approved tickets, use `editJiraIssue` to update **in parallel**:
- `summary` — corrected title
- `description` — corrected body (use `contentFormat: markdown`)
- `reporter` — set to Cali Kasten's account ID (look it up once with `lookupJiraAccountId`)

After all updates succeed, confirm which tickets were updated with links.

### 7. Add Attribution Comments

For each ticket whose summary or description was actually edited in step 6, use `addCommentToJiraIssue` to add a comment noting that it was re-worded by Claude, e.g. "This ticket was re-worded by Claude." Use `contentFormat: markdown`. Do this for every pushed ticket — it can run in parallel alongside or immediately after the `editJiraIssue` calls. Skip this for tickets that were left unchanged (already compliant, or skipped by the user).

# **Final Instructions**
1. **Always fetch reporter status** — set reporter to Cali Kasten on every ticket, compliant or not.
2. **Never push without approval** — always show drafts and get confirmation first.
3. **Flag but don't change issue types** — note Bug/Story mismatches for the user to fix manually.
4. **Infer, don't invent** — base drafted descriptions on the existing title and description only. If context is too thin to infer intent, note that in the draft and ask the user to fill it in.
5. **Push in parallel** — use simultaneous `editJiraIssue` calls for all approved tickets to minimize round trips.
6. **Attribute every edit** — always add a "re-worded by Claude" comment to any ticket whose content was actually changed — no exceptions.
