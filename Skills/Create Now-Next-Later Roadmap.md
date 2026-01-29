---
name: create-now-next-later-roadmap
description: Creates outcome-driven "Now, Next, Later" roadmaps that illustrate progress as predictions rather than rigid promises.
---

# **Purpose**
This skill facilitates the creation and maintenance of a "Now, Next, Later" roadmap. Unlike Gantt charts that create rigid deadlines, this format treats timelines as predictions, accounting for decreasing fidelity over time and focusing on outcomes rather than just feature lists.

## When To Use
- Use when communicating product vision and progress to executives and stakeholders.
- Use to align cross-functional teams (Product, Design, & Engineering) on upcoming priorities.
- Use when a Gantt chart is too rigid for the pace of development.
- Use during quarterly or monthly planning cycles to refresh the product trajectory.

# **Overall Agent Process**
1. **Inventory Problems:** Identify known units of work as problems to solve.
2. **Map to PDLC:** Categorize each problem into its current Product Development Life Cycle (PDLC) stage.
3. **Prioritize:** Perform an initial prioritization pass using an "Effort vs. Impact" matrix.
4. **Draft Roadmap:** Plot items into Now, Next, and Later columns.
5. **Collaborate & Refine:** Review with the user/stakeholders to identify missing items or priority errors.
6. **Define Roll-ups:** Organize work into Epics and Features that roll up into specific Goals & Objectives.
7. **Finalize Estimates:** Revisit scoping with Engineering and Design for level-of-effort (LOE) sizing.
8. **Output Artifact:** Present the roadmap in a structured, digestible format.

## Specific Process Details

### 2. Map to PDLC Stages
Use the following stages to determine work maturity:
- **Ideation & Brainstorming:** Discovery of new ideas and innovative solutions.
- **Validation:** Market research, surveys, and focus groups to ensure genuine need.
- **Product Design & Planning:** Sketching, wireframing, and creating blueprints.
- **Development & Testing:** Coding, QA, and user acceptance testing (UAT).
- **Launch:** Marketing strategy, distribution setup, and sales training.
- **Post-Launch Analysis:** Performance monitoring and continuous improvement.

### 4. Categorize by Time Horizon
- **Now:** High-fidelity work currently in Development or Testing. Held against present timelines.
- **Next:** Medium-fidelity work in Validation or Design. Consists of research, scoping, and upcoming builds.
- **Later:** Low-fidelity work in Ideation. Assumed value items that may pivot based on earlier learnings.

### 8. Output Format (Visual Layout)
Present the roadmap using a clear table or column structure:

```markdown
# **Product Roadmap: [Project/Initiative Name]**

| **NOW** (In-Progress / Predictions) | **NEXT** (Discovery / Scoping) | **LATER** (Assumptions / Backlog) |
| ----------------------------------- | ------------------------------ | --------------------------------- |
| **[Goal 1]**                        | **[Goal 2]**                   | **[Goal 3]**                      |
| - [Feature/Epic A]                  | - [Problem/Idea C]             | - [Potential Initiative E]        |
| - [Feature/Epic B]                  | - [Research Spike D]           | - [Potential Initiative F]        |
```

# **Final Instructions**
1. **Focus on Outcomes:** Ensure roadmap items are described as problems solved or value delivered, not just technical tasks.
2. **Predictions, Not Promises:** Remind users that "Next" and "Later" items decrease in fidelity and are subject to change.
3. **Audit Conjunctions:** Remove "and," "or," and "but" from roadmap item descriptions to maintain single-unit focus.
4. **Oxford Commas:** Use Oxford commas in all lists.
5. **Bullet Punctuation:** Ensure all descriptive bullet points end with a period.
6. **Title Case:** Use Title Case for all headers and roadmap column titles.
