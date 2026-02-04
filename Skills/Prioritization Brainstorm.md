---
name: prioritization-brainstorm
description: Facilitates a structured brainstorming session to prioritize problems, features, or tasks using prioritization frameworks.
---

# **Purpose**
This skill helps product managers and teams determine the optimal order of work at both macro (strategic) and micro (tactical) levels. It deconstructs complexity by applying the right prioritization framework to ensure maximum business value, user impact, and risk reduction.

## When To Use
- Use when a backlog or to-do list feels overwhelming or lacks clear direction.
- Use to align stakeholders on which features to build next (RICE/ICE).
- Use to sequence work for maximum economic benefit (WSJF).
- Use to identify high-impact root causes for complex problems (Pareto 80/20).
- Use for daily task management and distinguishing urgency from importance (Eisenhower).
- Use when comparing multiple potential solutions against specific criteria (Pugh Matrix).

# **Overall Agent Process**
1. **Identify the Level of Work:** Determine if the focus is on high-level strategy, feature roadmapping, or daily task execution.
2. **Diagnose the Right Framework:** Select the prioritization model (RICE, WSJF, Eisenhower, Pareto, ICE, Action-Priority, or Pugh) based on the context.
3. **Gather Core Inputs:** Collect data on risk, business value, user impact, dependencies, and effort.
4. **Apply Scoring/Categorization:** Execute the logic of the chosen framework to rank the items.
5. **Output Structured Results:** Present the prioritized list with a clear rationale for the rankings.

## Specific Process Details

### 2. Diagnose the Right Framework
- **Eisenhower Matrix:** Best for personal productivity and simple "to-do" lists. Focuses on Urgency vs. Importance.
- **Pareto Principle (80/20):** Best for problem-solving. Focuses on identifying the 20% of causes that result in 80% of the desired outcomes.
- **RICE Analysis:** Best for objective feature prioritization. Uses Reach, Impact, Confidence, and Effort.
- **ICE Analysis:** Best for early-stage idea vetting where criteria are weighted equally.
- **WSJF (Weighted Shortest Job First):** Best for sequencing work in flow-based systems (e.g., SAFe). Focuses on the Cost of Delay divided by Job Size.
- **Action/Priority Matrix:** Best for quick, visual grouping of items by Impact vs. Effort.
- **Pugh Matrix:** Best for choosing between several distinct alternatives or solution designs based on weighted criteria.

### 4. Apply Scoring/Categorization
- **RICE Score:** (Reach × Impact × Confidence) / Effort.
- **ICE Score:** Impact × Confidence × Ease.
- **WSJF Score:** (User-Business Value + Time Criticality + Risk Reduction/Opportunity Enablement) / Job Duration.
- **Pareto Logic:** Conduct a root cause analysis, group similar causes, and prioritize those representing the top 20% of impact.

### 5. Output Structured Results
Present results in a format that matches the framework's intent:
- **Matrix frameworks (Eisenhower, Action-Priority):** Use a 2x2 grid representation.
- **Scoring frameworks (RICE, WSJF):** Use a sorted table with individual component scores.
- **Pareto:** Identify the "Vital Few" vs. the "Useful Many."

# **Final Instructions**
1. **Challenge "Politics":** If "what the boss says" is the primary driver, proactively suggest using a data-driven framework (like RICE or Pugh) to provide a more objective perspective.
2. **Account for Risk:** Always include risk (bugs, compliance, security) as a high-priority factor in the brainstorming.
3. **Check for Conjunctions:** In prioritized items, remove "and," "or," and "but" to ensure each item is a single, clear unit of work.
