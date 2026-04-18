---
name: user-journey-map
description: Visually diagrams the path a user takes to reach a goal, mapping phases, touchpoints, pain points, and product surfaces in a structured table.
---

# **Purpose**
This skill helps product managers and UX designers visualize the process a person goes through to accomplish a goal. It clarifies needs, touchpoints, pain points, and how the experience unfolds across journey phases—scoped to the **journey map** itself, not downstream delivery planning.

## When To Use
- Use during the discovery phase to understand how a user currently achieves a goal.
- Use when designing a new feature to map out the anticipated user experience.
- Use to align the team on a shared mental model of the user's workflow.
- Use for **analytics, dashboards, and B2B reporting** flows—after **choosing phases** that fit the scenario, those journeys are _often_ well described as _Trigger → Frame → Interpret → Decide → Institutionalize_ (or **Act**), but the steps should still be **validated**, not assumed.
- Use for **in-product / portal journeys** (login → specific pages → modules) with the **portal-style table** below when the deliverable is a compact map of screens, UI components, and external systems.

# **Overall Agent Process**
1. **Identify the Actor:** Define the specific persona (one point of view per map).
2. **Define the Scenario & Outcome:** Clarify the specific situation, the goal, and what success looks like. Optionally capture **job to be done**, **constraints** (e.g., comparable time periods, defensible metrics), and a **north-star outcome** for stakeholder-ready conclusions.
3. **Determine Journey Steps (horizontal axis):** **Figure out the right phase names and count** for this persona and scenario _before_ filling the table. Each column should reflect a **real shift in intent or mode of work** (not a dump of every screen). Aim for **3–5 narrative stages** unless the user explicitly wants more (e.g. **Interpret** split into sub-lenses—see below). Use **plain-language labels** the persona would recognize; pull vocabulary from the user when they have given it.
   - **Data-heavy default (suggest, then validate):** For **most workflows centered on data**—reporting, KPIs, exploration in BI or analytics products, “did we improve?”, exec readouts, monitoring a metric over time—**start by proposing taxonomy B:** **Trigger → Frame → Interpret → Decide → Institutionalize** (or **Act** for the last column if that matches how they talk about follow-through). Add **one short sentence** in the artifact (e.g. under **Scenario** or **Notes**) on why those stages fit _this_ scenario.
   - **If it doesn’t fit:** Say so and switch or blend—e.g. funnel (taxonomy A) for purchase/adoption, operational shorthand (C) for internal tooling, or **rename/merge** stages (e.g. combine Frame + first Interpret beat) when the user’s flow is simpler or collaboration-heavy.
   - **Table columns:** one column per agreed stage _unless_ **Interpret** is split into explicit sub-lenses; that yields more columns but stays one logical **Interpret** stage.
4. **Detail Journey Dimensions (vertical axis):** For each phase column, fill the rows using either the **generic** row set or the **portal / in-product analytics** row set (see **Output rows**).
5. **Output Structured Map:** Present the journey using the **appropriate table template**; add optional banner, swimlane, or metrics sections when useful. Follow **Markdown Table Formatting** (this skill) for every journey table.

## Journey Taxonomies

Use the taxonomies below as **menus and definitions**, not as a mandate. Step 3 is where you **justify** which phases appear as columns.

### A. Classic Funnel (B2C Lifecycle and Broad B2B)
Examples: **Awareness → Consideration → Purchase → Retention → Advocacy**; or shorter **Discover → Evaluate → Purchase → Onboarding**.

Use when the journey is about **buying, adopting, or championing** a product or program.

### B. Analytics Workflow (Reporting and Insights)
**Suggested phases for most data-centric journeys** (validate against the scenario): **Trigger → Frame → Interpret → Decide → Institutionalize**

| Phase | What it means |
| ----- | ------------- |
| **Trigger** | Why the session starts (calendar, alert, leader ask, incident). User should be able to state what decision this work informs. |
| **Frame** | Scope the analysis: entity (brand, SKU set), time window, surfaces/channels, metric definitions, comparability guardrails. |
| **Interpret** | Turn metrics into meaning: trend, magnitude, drivers, segments, exemplar evidence, sanity checks. |
| **Decide** | Commitments: priorities, owners, deadlines, escalations; what _not_ to do. |
| **Institutionalize** | Repeatability: saved views, scheduled reports, definitions/glossary, alerts, cadence with stakeholders. |

**Act:** Use **Act** when the narrative emphasizes **concrete next steps** (brief stakeholders, schedule follow-up, request content changes, re-enter the product on a cadence) rather than “institutionalize” language. Same column intent; pick one label per map.

**Interpret sub-lenses:** When the user needs separate columns for different analytic cuts — treat them as **one mental Interpret stage** split for readability. Do **not** rename unrelated work as extra top-level taxonomies just to add columns.

Use when the journey is about **logging into a tool, reviewing performance, comparing periods, and acting on data** — not a retail checkout. UI steps (login, filters, export) sit _inside_ these phases, usually under **Frame** and **Interpret**.

### C. Operational Shorthand
Examples: **Plan → Execute → Review → Report.** Use for internal tooling when neither A nor B fits cleanly.

## Specific Process Details

### Output Rows (vertical axis)

**Generic journey (funnel, broad workflow)** — for each phase column, consider:

- **What they do** — Observable actions (not only clicks; include thinking work like “sanity-check baseline”).
- **Touchpoints** — Screens, emails, Slack, docs, exports, meetings.
- **Thinking (quotes)** — Short first-person lines that capture questions and hypotheses.
- **Emotion** — High-level affect (urgency, confidence, skepticism, frustration).
- **Pain points** — Friction, ambiguity, distrust in data, handoff gaps.
- **Opportunities** — Product, design, or content improvements implied by the journey.

**In-product** — use when mapping **login → product areas → specific UI modules** and handoffs to tools outside the product. Default to this row set for dashboard and reporting journeys unless the user asks for the generic rows.

- **User Actions** — What the person does in that phase (including cognitive work), with **bold** on the highest-signal verbs and nouns.
- **In-Product** — Named screens or areas (e.g. log in, home, specific product pages or tabs). Use **—** if none.
- **Key Components & Features** — Charts, tables, filters, overlays, KPI clusters, named sections. Use **—** if none.
- **External** _(systems outside [product name])_ — Email, Slack/Teams, data vendors, spreadsheets, meetings—not part of the core app. Use **—** if none.
- **Pain Points** — Same intent as generic row; include distrust-in-data and scope ambiguity where relevant.
- **Thoughts / Reactions** — Short first-person questions or reactions (same role as **Thinking (quotes)** in the generic template).

Use **Title Case** for row labels that are proper product labels and stay consistent within one artifact (**User actions** vs **User Actions** — pick one).

**Placeholders:** Use **NEEDS REVIEW** in a cell only when information is genuinely unknown and the user or PM has marked a gap; otherwise infer from context or ask **one** clarifying question before drafting.

### Optional Additions
- **Context banner** above the table: scenario one-liner, constraints, success definition—or use **`### Scenario`** and **`### Expectations`** (or **Success**) as subsections before the table for stakeholder-ready maps.
- **Swimlanes** — Same phases, multiple actors (e.g., brand owner, agency, leadership) for handoff-heavy **Decide** stages.
- **Metrics row** — Time-to-answer, repeat usage, definition-related support load, etc., if the map is product-led.

## Markdown Table Formatting

**Use this format for every user journey map table** unless the user explicitly asks for something else (e.g. slide export, transposed layout). Goals: readable in source control, clean in preview, no wide “ASCII art” padding.

- **Stages = columns; dimensions = rows.** First header cell may be empty (`| |`).
- **No column padding:** never pad cells with spaces to align pipes; one space after each `|` is enough.
- **Separator row:** only `| --- | --- | ... |` (no extra-long dashed cells).
- **Empty / N/A cells:** em dash **—** (not `--`).
- **Line breaks inside cells:** use HTML `<br>`. Stack **distinct actions, pages, questions, or blocks** with **double breaks** **`<br><br>`** so there is a clear visual gap between items (e.g. separate user actions, separate portal pages, separate evidence paths). Do not rely on long single-line paragraphs in cells.
- **Inline bullet lists using `•`:** do not run items as `foo • bar • baz` on one line. Put the **first** segment first, then **`<br>•`** before each additional item (e.g. KPI cluster lines, Growth Drivers sub-bullets).
- **Italics vs bold in tables:** use **single-underscore** `_italic_` for light emphasis (parentheticals, qualifiers). Use **`**bold**`** for load-bearing terms (actions, page names, metrics). Do not use `*italic*` in journey tables if `_italic_` will work—keeps emphasis unambiguous next to `**bold**`.
- **Scannable emphasis:** bold only the highest-signal words per cell; avoid bolding entire cells.

## Standard Output Template: Classic Funnel

Present the journey map in structured markdown. Adjust row labels if the team prefers fewer rows (e.g., merge Thinking + Emotion).

```markdown
# **Customer Journey Map: [Scenario name]**

**Persona:** [Name / role]  
**Job To Be Done:** [What they need to accomplish in plain language]  
**Success:** [Observable outcome — e.g., defensible MoM readout + committed next step]

| | **[Phase 1]** | **[Phase 2]** | **[Phase 3]** | **[Phase 4]** | **[Phase 5]** |
| --- | --- | --- | --- | --- | --- |
| **What they do** | | | | | |
| **Touchpoints** | | | | | |
| **Thinking (quotes)** | | | | | |
| **Emotion** | | | | | |
| **Pain points** | | | | | |
| **Opportunities** | | | | | |
```

**Example phase headers (analytics workflow):** Trigger → Frame → Interpret → Decide → Institutionalize (or **Act**).

**Example phase headers (funnel):** Awareness → Consideration → Purchase → Retention → Advocacy.

**Example phase headers (Interpret split):** Trigger → Frame → Interpret — Summary → Interpret — [Lens 2] → … → Decide → Act.

## Standard Output Template: Analytics Workflow

Use when the journey is anchored in **named product surfaces** and **UI modules**. Adjust the number of phase columns to match the taxonomy (including Interpret sub-lenses if needed).

```markdown
# [Journey set or product area title]

## [Persona name], [Role]

### Scenario

[Specific situation and why they entered the flow.]

### Expectations

[What they need to understand or leave with—success from their point of view.]

| | **[Phase 1]** | **[Phase 2]** | **…** | **[Final phase]** |
| --- | --- | --- | --- | --- |
| **User actions** | | | | |
| **Portal pages** | | | | |
| **Key components & features** | | | | |
| **External** _(systems outside [Product])_ | | | | |
| **Pain points** | | | | |
| **Thoughts / reactions** | | | | |

```

# **Final Instructions**
1. **Focus on one persona:** If the user maps multiple roles in one artifact, suggest separate journeys or add swimlanes with a single primary actor per narrative.
2. **Discover steps before cells:** Do not jump straight to a filled table; **lock phase names** (and why they fit) first. For **data-related** journeys, **propose Trigger → Frame → Interpret → Decide → Institutionalize/Act** when it fits, and **adapt** when it does not.
3. **Prefer breadth over click-by-click steps** for stage names; put granular UI steps in **User actions** / **What they do** (and **Portal pages** / **Key components & features** in the portal template) for the relevant phase.
4. **Pick the row set deliberately:** Generic vs **portal / in-product analytics**—default the latter for **analytics, dashboards, and B2B reporting** in a named product.
5. **Ask before drafting:** If persona, scenario, or success is unclear, ask clarifying questions first. If **only** the phase model is ambiguous (e.g. funnel vs analytics), state a **recommended** column set and offer an alternative in one line rather than blocking.
6. **Format preference:** If the user will paste into Miro or a slide, offer **stages as rows** instead of columns on request—same content, transposed layout.
7. **Apply Markdown table formatting** per **Markdown Table Formatting** above: compact pipes, `—` for empty cells, `<br><br>` between stacked items, `<br>•` for `•`-style sub-lists, and `_` / `**` for italics vs bold.
