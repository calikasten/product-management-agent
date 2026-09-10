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
- Time range: **past 7 days** (`created >= -7d`)
Use `searchJiraIssuesUsingJql` with fields: `summary`, `description`, `issuetype`, `status`, `assignee`, `created`. Request up to 50 results. Use `responseContentFormat: markdown`.

### 2. Audit Each Ticket

For each ticket, check the following based on its Jira issue type:

#### Story (issue type: "Story")
The description must contain all of the following:
- `**As a**` ... `**I want**` ... `**so that**` — one-line user story statement
- Acceptance criteria header — either `**Acceptance Criteria:**` **or** incrementally numbered blocks. Both formats are compliant. For numbered blocks, the entire label plus description must be bolded as one unit — `**AC #1: <description>**` — not just the `AC #1:` label with a plain-text description after it.
- `GIVEN` / `WHEN` / `THEN` — all caps, no bullets, each on its own line separated by a hard return/carriage return (an actual line break, not just wrapped text within one paragraph)

Flag if any of these are missing or if the description is empty. Also flag GIVEN/WHEN/THEN clauses that are present but run together without a hard return between them (e.g. merged into one line or one paragraph).

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
- **Reporter:** Should be set to Cali Kasten (`5f15b1e8591bbc001bcc4dd1`). Flag if not set to her.
- **Team member names:** Do not include role qualifiers. Write "Jessie", not "Jessie (SVP)".

### 3. Report Violations

Present a table or list showing:
- Ticket key + linked summary
- Issue type
- What's wrong (e.g., "Empty description", "Missing GIVEN/WHEN/THEN", "Title not title case", "Spike missing Timebox")

Clearly separate tickets that are **fully compliant** from those that **need fixes**.

### 4. Draft Fixes

For each non-compliant ticket, draft:
1. A corrected **summary** (proper title case; spike prefix if applicable)
2. A corrected **description** using the appropriate template

**When drafting from sparse context (e.g., empty description):** Infer intent from the title. Use the correct persona defaults:
- **Foundry engineer** — for backend, data pipeline, or infrastructure work
- **Foundry PM** — for internal tooling or process stories
- **Agentic Discovery app user** — for dashboard or brand-facing features

**Voice:** PM-to-eng tone. Short clauses. `**I want**` = tight hook. `**so that**` = one plain-language benefit. One GIVEN/WHEN/THEN for the main behavior; edge cases go in Notes.

**Do not** include team member role qualifiers (e.g., write "Jessie", not "Jessie (SVP)").

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
- `reporter` — always set to `{"id": "5f15b1e8591bbc001bcc4dd1"}`

Cloud ID: `0ec0c56c-e73e-483d-9aeb-4b4741d9749e`

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
