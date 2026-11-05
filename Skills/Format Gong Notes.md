---
name: format-gong-notes
description: Converts a pasted Gong call transcript into a formatted meeting note matching the existing template, and saves it into the correct Meeting Notes subfolder.
---

# **Purpose**
Converts a pasted Gong call transcript (title, participants, timestamped dialogue) into a structured meeting note — Overview with Goal/Key Takeaways/Next Steps, followed by a chronological Discussion Topics breakdown — matching the format already used in the target Meeting Notes folder, and saves it as a new `.md` file in that folder.

## When To Use
Use this skill when the user pastes a Gong call transcript (or shares a Gong recording's transcript text) and asks to turn it into a meeting note. Do not use this skill for live meeting notes not sourced from a transcript, for editing an existing note in place, or when the user wants a different output format (e.g., a Jira ticket, an executive summary, a Slack recap) — those are separate skills.

# **Overall Agent Process**
1. **Identify Target Folder:** Determine which Meeting Notes subfolder the note belongs in.
2. **Read Template Examples:** Read 2-3 of the most recent existing notes in that folder to confirm current formatting conventions before writing.
3. **Extract Metadata:** Pull the call date, company/attendee names, and (if present) the Gong recording URL from the transcript header.
4. **Determine Filename:** Construct the filename from the date and a concise meeting title.
5. **Draft the Note:** Write Overview (Goal, Key Takeaways, Next Steps & Action Items) and Discussion Topics (chronological ## sections) from the transcript content.
6. **Save the Note:** Write the finished note as a new file in the target folder.

## Specific Process Details

### 1. Identify Target Folder
Default target folder is:
`{MEETING_NOTES_FOLDER}` ← replace with the full path to your default meeting notes folder

If the transcript content or user's request clearly indicates a different program or project, ask the user which subfolder to use rather than guessing — do not invent a new folder.

### 2. Read Template Examples
Before drafting, read the 2-3 most recently modified `.md` files already in the target folder (by file mtime) to confirm current section structure, heading style, tag conventions, and tone. Formatting conventions can drift over time — always check current examples rather than relying on memory of a past note.

### 3. Extract Metadata
From the transcript header, extract:
- **Call date** — from a line like "Recorded on [Month] [Day], [Year]"; convert to `YYYY-MM-DD`.
- **Attendees/company** — from the Participants list; identify which participants are from the user's company and which are from the external company (external company name is what goes in the filename and note body).
- **Gong recording URL** — only if the user has pasted or provided one alongside the transcript. Do not fabricate or guess a URL. If none is provided, omit the `[VIEW RECORDING](...)` line entirely (some existing notes may lack this line — that's an acceptable pattern, not an error).

### 4. Determine Filename
Format: `YYYY-MM-DD {Company} {Meeting Topic}.md`, e.g. `2026-07-30 Acme Product Demo.md`.
- `{Company}` is the external company name (not the user's company).
- `{Meeting Topic}` is a short descriptor inferred from the transcript content and existing naming patterns in the folder — e.g. "Product Demo," "Beta Customer Feedback Session," "Demo & Pricing," "Pilot Check In." Pick whichever best matches the call's actual content (first intro/demo call vs. a pricing-focused follow-up vs. a feedback session, etc.) and stays consistent with how similar past calls in the folder were named.

### 5. Draft the Note
Follow this exact structure (matching current examples read in step 2):

```markdown
---
Tags:
  - [tag matching the folder's existing notes]
---
# Overview
[VIEW RECORDING](gong-url)  <!-- omit this line entirely if no URL was provided -->

**Goal:** [1 sentence: purpose of this specific call.]

**Key Takeaways:**
- **[Short bolded label]:** [2-4 sentences synthesizing what happened, why it matters, and any tension or nuance — not just a restatement of what was said.]
- [Continue for each major theme, ordered roughly by importance/impact. Typically 4-7 bullets.]

**Next Steps & Action Items:**
- [External Company]:
    - [Action item.]
- [Your Company]:
    - [Action item.]

---
# Discussion Topics

## [Section Title Matching Chronological Flow of Call]
- [Bullet detail, written in third person past tense, capturing specifics — names, numbers, product/feature names, direct concerns raised, and how they were answered.]

## [Next Section Title]
- ...
```

Writing guidance:
- **Key Takeaways** should synthesize, not transcribe — capture the "so what," not just "what was said." Include tensions, objections, and open questions, not only positive signal.
- **Next Steps & Action Items** must be grouped by party (the external company first, then the user's company), each as a nested bullet list of concrete owned actions.
- **Discussion Topics** should mirror the actual chronological arc of the call (e.g., Introductions, Demo walkthrough by product area, Objections/Q&A, Pricing/Next Steps) with one `##` section per phase. Use full sentences, attribute specific points to specific speakers by name where it adds clarity (especially objections, questions, or commitments), and preserve concrete details (numbers, product names, competitor names, dates) exactly as stated in the transcript.
- Do not include filler, small talk, or verbatim transcript text — synthesize into clean prose.
- Never invent facts, figures, dates, or URLs not present in the transcript or supplied by the user.

### 6. Save the Note
Write the file directly into the target folder identified in step 1, using the filename constructed in step 4. Do not overwrite an existing file with the same name — if one exists, flag the collision to the user instead of silently overwriting.

# **Final Instructions**
1. Always read current examples from the target folder (step 2) before drafting — do not rely solely on this skill's embedded template, since folder conventions may evolve.
2. Ask the user for the Gong recording URL if they haven't provided one and it seems likely to exist; otherwise proceed without it.
3. Ask clarifying questions only if the target folder or company identity is genuinely ambiguous from the transcript — otherwise proceed autonomously through drafting.
4. Apply relevant guidance from `effective-writer` for clarity and concision in the synthesized prose.
