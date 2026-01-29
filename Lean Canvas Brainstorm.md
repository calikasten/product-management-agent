---
name: lean-canvas-brainstorm
description: Facilitates a structured Lean Canvas brainstorming session to deconstruct product ideas into actionable business models, identifying market demand, core problems, and unique value.
---

# **Purpose**
This skill helps product managers and founders quickly iterate on business models using the Lean Canvas framework. It replaces long business plans with a one-page summary of key assumptions, focusing on problem-solution fit and market demand.

## When To Use
- Use when evaluating a new startup or product idea.
- Use to pivot an existing product by re-evaluating core assumptions.
- Use during discovery to identify early adopters and critical pain points.
- Use when a high-level concept needs to be communicated to stakeholders or investors.

# **Overall Agent Process**
1. **Gather Initial Context:** Receive the product idea or problem statement.
2. **Ask Clarifying Questions:** Before drafting, ask questions to narrow down customer segments and early adopters.
3. **Draft the Canvas:** Attempt to fill all 9 blocks. Use the "5-Whys" technique to drill down into the **Problem** section.
4. **Suggest Segment Splits:** If the audience is too broad, proactively suggest creating separate canvases for distinct segments (e.g., Drivers vs. Riders for Uber).
5. **Format Output:** Present the final canvas using the Markdown ASCII-art layout provided in the specific process details.

## Specific Process Details

### 2. Ask Clarifying Questions
- Focus on identifying the "Early Adopters"—those with an "above average" need for the product.
- Identify "Existing Alternatives" (not just direct competitors, but how they solve the problem today, e.g., "walking" as an alternative to "Uber").

### 3. Deep Dive into Problems (5-Whys)
For the top 1–3 problems, perform a "5-Whys" analysis to reach the root cause.
- **Example:** "It's hard to find parking" -> Why? -> "Too many cars in the city center" -> Why? -> "Public transit is unreliable" -> Why? ... until a core, solvable pain point is found.

### 5. Format Output (The Layout)
Use the following ASCII/Code-block structure for the final output to mimic the Lean Canvas visual layout:

```markdown
| PROBLEM | SOLUTION | UNIQUE VALUE PROPOSITION | UNFAIR ADVANTAGE | CUSTOMER SEGMENTS |
| :--- | :--- | :--- | :--- | :--- |
| **1.** [Problem 1] | **1.** [Solution 1] | [Single, clear, compelling message] | [Something that cannot be easily copied] | [Target customers] |
| **2.** [Problem 2] | **2.** [Solution 2] | | | |
| **3.** [Problem 3] | **3.** [Solution 3] | | | |
| | | **HIGH-LEVEL CONCEPT** | | **EARLY ADOPTERS** |
| **EXISTING ALTERNATIVES** | **KEY METRICS** | [X for Y analogy] | **CHANNELS** | [Ideal characteristics] |
| [How problems are solved today] | [Numbers that track success] | | [Path to customers] | |

| COST STRUCTURE | REVENUE STREAMS |
| :--- | :--- |
| [Fixed and variable costs] | [Sources of revenue and pricing model] |
```

# **Final Instructions**
1. **Be Proactive with Segments:** If a user says "This is for everyone," push back and suggest a specific "Early Adopter" group.
2. **Focus on Outcomes:** Ensure the **Unique Value Proposition** focuses on benefits, not just features.
3. **Check for Conjunctions:** Remove "and," "or," and "but" from the Value Proposition to keep it sharp.
4. **Apply Oxford Commas:** Use Oxford commas in all lists.
5. **Bullet Punctuation:** Ensure all descriptive bullet points end with a period.
