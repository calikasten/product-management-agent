---
name: risk-mitigation-plan
description: Facilitates risk identification and mitigation using pre-mortems, anti-pattern detection, and structured likelihood vs. impact matrices to safeguard project success.
---

# **Purpose**
This skill helps product managers proactively identify, categorize, and mitigate threats to project, team, and business success. By combining the "Pre-Mortem" framework with a structured Risk Assessment Matrix, it shifts the focus from reacting to failures to preventing them through strategic foresight.

## When To Use
- Use early in a project's lifecycle (Discovery or On Deck phases).
- Use before a major launch or pivot.
- Use when the team feels "stuck" or exhibits anti-patterns (e.g., Analysis Paralysis, Group Think).
- Use to align stakeholders on the most critical threats and their corresponding mitigation owners.

# **Overall Agent Process**
1. **Detect Anti-Patterns:** Audit the current project state for common macro, management, and engineering anti-patterns.
2. **Conduct a Pre-Mortem:** Prompt the team to assume the project has "spectacularly failed" and brainstorm why.
3. **Categorize Threats:** Group identified risks into "Tigers," "Paper Tigers," and "Elephants."
4. **Map the Risk Landscape:** Categorize risks as Strategic, Operational, Financial, or External.
5. **Score Likelihood & Impact:** Plot the risks against a 3x3 or 5x5 matrix to determine their influence.
6. **Draft the Mitigation Plan:** Identify risk indicators, mitigation actions, and clear owners for high-priority threats.
7. **Output Visual Diagram:** Present the final visual diagram of the risk assessment matrix.

## Specific Process Details

### 1. Detect Anti-Patterns
Scan for these common project jeopardy indicators:
- **Macro:** Analysis paralysis, putting the cart before the horse, group think.
- **Management:** Micromanaging, seagull management.
- **Organization:** Operating in silos, vendor lock-in, gold-plating.
- **Engineering:** Viewgraph engineering, fire drills, death marches, intellectual violence.

### 2. Conduct a Pre-Mortem
Facilitate a session using these failure archetypes:
- **Tigers:** Real, high-impact threats that can kill the project.
- **Paper Tigers:** Perceived threats that sound scary but have little real impact.
- **Elephants:** Obvious, major problems that everyone knows about but no one is discussing.

### 4. Map the Risk Landscape
Categorize risks using these key dimensions from the SPINS PM framework:
- **Feasibility:** Technical constraints, integration risks, and scalability.
- **Viability:** Business model, monetization, compliance, and supportability.
- **Go-to-Market:** Marketing channels, value proposition, and launch timing.
- **Strategy & Objectives:** Strategic alignment, competitive response, and external factors (Inflation, AI, Laws).
- **Usability & Value:** User onboarding, cognitive load, and sustained value creation.
- **Team & Ethics:** Personnel risks, tool gaps, and ethical considerations.

### 5. Score Likelihood & Impact
Plot risks based on two criteria:
- **Likelihood:** The level of probability (1–5) the risk will occur.
- **Impact:** The level of severity (1–5) if the risk is realized.
- **Priority:** High-likelihood/High-impact risks (top right quadrant) must be addressed first.

### 7. Output Visual Diagram
Present high-priority risks in this format:

```markdown
| Risk Category   | Threat Description           | Likelihood | Impact | Mitigation Action            | Owner       |
| --------------- | ---------------------------- | ---------- |------- | ---------------------------- | ----------- |
| [Strategic/Ext] | [Tiger/Elephant description] | [1-5]      | [1-5]  | [Specific preventative step] | [Name/Role] |
```

# **Final Instructions**
1. **Assume Failure:** In pre-mortems, start by transporting the team to a future where the project has already failed to unlock more honest brainstorming.
2. **Challenge Comfort:** Proactively look for "Elephants" that stakeholders might be avoiding.
3. **Evidence over Intuition:** Use the Likelihood/Impact matrix to move past subjective fears toward data-driven prioritization.
