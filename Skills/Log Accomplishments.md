---
name: log-accomplishments
description: Reviews a month of shipped Jira work, local meeting notes, and Fathom recordings to identify the user's career-worthy accomplishments, drafts them in the established accomplishments-note format, and (after approval) adds them under that month in the yearly "YYYY Accomplishments.md" note.
---
# **Purpose**
Keeps the user's yearly accomplishments log current by turning one month of shipped work and meeting evidence into a few high-signal, outcome-focused bullets, written in the same style as prior entries, and adding them to the correct month in the yearly note.

## When To Use
Use this skill when the user asks to log, update, capture, or write up their accomplishments (or "wins") for a month, or when running the monthly accomplishments update.

Do not use this skill for:
- Team-facing status reports (use `stakeholder-update`, `executive-update`, or `sprint-review-summary`).
- Customer-facing release notes (use `release-notes`).
- Writing a self-review, promotion case, or resume from scratch. This skill only maintains the monthly log, although those documents can be built from the log afterwards.

# **Overall Agent Process**
1. **Determine Target Month and File:** Identify the month to cover and the yearly note to update.
2. **Read the Notes for Format and Context:** Read the target yearly note and the prior year's note to learn the format and see what is already logged.
3. **Gather Jira Evidence:** Fetch tickets that moved to Shipped during the target month.
4. **Gather Meeting Note Evidence:** Read local meeting notes dated within the target month.
5. **Gather Fathom Evidence:** Pull summaries of Fathom recordings from the target month that aren't already covered by local notes.
6. **Select Worthwhile Accomplishments:** Group evidence into themes and keep only the career-worthy ones.
7. **Draft and Present for Review:** Show the drafted month section, with sources, and wait for approval.
8. **Write to the Note:** After approval, insert the section in the correct position in the yearly note.
9. **Flag Empty Months:** Point out any other month sections that are empty placeholders and offer to fill them.

## Specific Process Details

### 1. Determine Target Month and File
- **Default month:** the last full calendar month before today. For example, running on 2026-11-02 covers October 2026. If the user names a month, use that instead.
- **Target file:** chosen by the target month's year, not today's year (running in January 2027 for December 2026 updates the 2026 file):
  `{ACCOMPLISHMENTS_FOLDER}/{YYYY} Accomplishments.md` ← replace `{ACCOMPLISHMENTS_FOLDER}` with the full path to your accomplishments folder
- **Reference file:** the prior year's note in the same folder, e.g. `2025 Accomplishments.md`.
- If the paths contain spaces or special characters, always quote them in shell commands.
- If the target year's file does not exist, create it at the write step (step 8) with the same frontmatter as the prior year's note, then add the month section.

### 2. Read the Notes for Format and Context
Read the target yearly note in full, and also the prior year's note. Use them to learn:
- **What is already logged.** Do not repeat an accomplishment that already appears in an earlier month (e.g., if "Shipped the free tier" is under July, don't re-log it in October). A follow-on milestone with new impact (e.g., free tier reached N sign-ups) is fine.
- **Whether the target month already has content.** If the month has real bullets, treat this run as an addition: propose only new bullets and never rewrite or remove existing ones. If the month is only a placeholder (`* ` with nothing after it), replace the placeholder.

**Format conventions (match exactly):**
- YAML frontmatter with `Tags:` at the top. Leave it unchanged.
- Each month is an H1 heading with the month name only: `# October`.
- Months run in **reverse chronological order**, so the newest month is at the top, right below the frontmatter.
- Top-level bullets use `* ` (asterisk + space). Each one is a single accomplishment, starting with a past-tense action verb such as Shipped, Led, Completed, Delivered, Created, Improved, Guided, Gained alignment, Coached, Onboarded, or Presented.
- Sub-bullets use a **tab** followed by `* ` (`\t* `). They hold impact, metrics, scope, or business value. One level of nesting is typical and two is occasional. Don't go deeper.
- Usually **1–4 top-level bullets per month**, each with 0–3 sub-bullets.
- Quantify wherever the evidence supports it, using the established styles: before → after (`55% → 87%`), percent change (`+14% improvement in ...`), scale (`from 1.62M to 4.8M`), multipliers (`a 36x increase!`), or speed in bold (`**in 3 months**`).
- Lead with the outcome or business value, not implementation detail. Name the business effect where it is known: revenue, customer adoption, a "first" for the company, cross-functional alignment, or time saved.
- Never add image embeds. The user adds those manually.
- Match the spacing between month sections already used in the target file.

### 3. Gather Jira Evidence
Ask which Jira project(s) to search if the user hasn't specified. Use the Atlassian MCP tool `searchJiraIssuesUsingJql` (look up the Cloud ID with `getAccessibleAtlassianResources`; `responseContentFormat: markdown`, up to 100 results; paginate if more):

```
project = {PROJECT_KEY} AND status changed to "Shipped" during ("YYYY-MM-01", "YYYY-MM-<last day>") ORDER BY updated ASC
```

Retrieve `summary`, `description`, `issuetype`, `parent`, and `labels`. If the query returns nothing, fall back to `project = {PROJECT_KEY} AND status = Shipped AND resolved >= "YYYY-MM-01" AND resolved <= "YYYY-MM-<last day>"`, and say in the draft that you used the fallback.

Group tickets by parent epic or theme. Epic summaries and descriptions are often the best source of the "why" and the business value, so fetch the parent epic when the child tickets alone don't explain it.

### 4. Gather Meeting Note Evidence
Root folder: `{MEETING_NOTES_FOLDER}` ← replace with the full path to your meeting notes folder (include its subfolders).

- Filenames start with the meeting date: `YYYY-MM-DD <Meeting Topic>.md`. Find every `.md` file whose date prefix falls within the target month, e.g. `find "<root>" -name "YYYY-MM-*.md"`.
- Read each note's Overview / Key Takeaways / Next Steps first, and read further only when a takeaway looks like an accomplishment.
- Look for evidence such as:
  - A launch, release, or milestone reached (beta, GA, first customer, integration live).
  - Customer outcomes: customers onboarded, positive feedback, renewals or conversions, measured results.
  - The user leading or facilitating something notable: workshops, design partner sessions, cross-team alignment, decisions unblocked, strategy adopted.
  - Sales and GTM contributions: demos led, pricing or packaging decisions, enablement delivered.
  - Mentoring or coaching outcomes, and knowledge-sharing presentations.
  - New partnerships or integrations.

### 5. Gather Fathom Evidence
- Use `list_meetings` from the Fathom MCP server with `created_after` / `created_before` set to the target month's bounds and `include_summary: true`. Don't filter by recorder, because the user may have joined meetings someone else recorded.
- Skip recordings that a local meeting note from step 4 already covers (same date and an equivalent topic or company).
- Use the summaries the same way as the meeting notes in step 4. Call `get_meeting_transcript` only to verify a specific claim or metric before using it in a bullet. Never state what someone said without tool evidence.
- If Fathom is unavailable or not authenticated, continue with Jira and the local notes, and mention in the draft that Fathom was skipped.

### 6. Select Worthwhile Accomplishments
Merge the evidence into themes, since several tickets and meetings usually support one accomplishment. Keep a theme only if it passes at least one of these tests:
- **Business impact:** revenue, pricing or monetization, customer acquisition, conversion, or retention.
- **Customer outcome:** measurable results for customers, customers onboarded, or proof points.
- **Launch or first:** a new capability, release milestone, or first-of-its-kind for the company.
- **Leadership:** the user led, facilitated, aligned, or unblocked cross-functional work or decisions.
- **People:** mentoring, coaching, hiring, or knowledge sharing.
- **Measurable improvement:** accuracy, speed, scale, or cost with a number attached.

Exclude bug fixes, chores, refactors without a measurable result, small UI tweaks, routine recurring meetings with no outcome, and in-progress work. Several minor tickets can roll up into one bullet when they add up to a meaningful capability.

Aim for **1–4 top-level bullets**, choosing the strongest rather than listing everything. Only include metrics that appear in the evidence, and never invent or estimate numbers. If a bullet would be stronger with a metric you don't have, write it without the number and mention in the review step that it could be added.

### 7. Draft and Present for Review
Show the user, in chat:
1. **The drafted month section**, exactly as it would appear in the file (in a markdown code block so tabs and `* ` markers are visible).
2. **Sources** for each top-level bullet: the Jira keys and the meeting note filenames or Fathom meeting titles.
3. **Considered but left out:** a short list of candidate items that didn't make the cut, each with a one-line reason, so the user can pull one back in.
4. **Gaps:** any metrics that would strengthen a bullet, and any sources that were skipped (e.g., Fathom unavailable).

Wait for the user to approve or edit. Apply the requested changes and show the revised section again if the edits were substantial.

### 8. Write to the Note
After approval, edit the yearly note with the Edit tool (not shell commands, since the file uses tabs):
- **Month section exists:** replace its placeholder, or append the new bullets below the existing ones.
- **Month section missing:** insert `# <Month>` plus the bullets in reverse chronological position, directly above the most recent earlier month that is present. If no earlier month exists, insert it at the bottom.
- Leave the frontmatter, all other months, and any image embeds unchanged.

Confirm what was written and give the file path.

### 9. Flag Empty Months
After writing, scan the yearly note for month sections whose only content is an empty placeholder (`* ` with nothing after it), and for missing months between January and the target month. List them and offer to run this skill for each one. Don't fill them without the user's go-ahead.

# **Final Instructions**
1. Never write to the accomplishments note before the user approves the draft.
2. Match the existing format exactly: `# Month` headings, newest month first, `* ` bullets, tab-indented `* ` sub-bullets, outcome-first wording that starts with a past-tense verb.
3. Choose the strongest 1–4 accomplishments rather than listing everything.
4. Never invent metrics, quotes, or outcomes. Every bullet must trace back to a Jira ticket, meeting note, or Fathom recording, and those sources go in the review draft, not in the note.
5. Don't duplicate accomplishments already logged in an earlier month.
6. Never remove or rewrite existing bullets, frontmatter, or image embeds in the note.
