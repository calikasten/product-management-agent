---
name: create-customer-journey-map
description: Visually diagrams the path a user takes to reach a goal, identifying core activities, tasks, and the critical user stories required for delivery.
---

# **Purpose**
This skill helps product managers and UX designers visualize the process a person goes through to accomplish a goal. By mapping the journey from persona to specific user stories, it clarifies the user's needs, identifies pain points, and defines the critical path for product delivery.

## When To Use
- Use during the discovery phase to understand how a user currently achieves a goal.
- Use when designing a new feature to map out the anticipated user experience.
- Use to align the team on a shared mental model of the user's workflow.
- Use to identify which user stories are essential for the MVP vs. which can be deferred.

# **Overall Agent Process**
1. **Identify the Actor:** Define the specific persona (one point of view per map).
2. **Define the Scenario & Outcome:** Clarify the specific situation and the goal the actor wants to achieve.
3. **Map Journey Phases:** Outline the high-level stages or core activities in the process.
4. **Detail Actions & Mindsets:** For each phase, describe the specific tasks the user performs and what they are thinking or feeling (including "what they want to avoid").
5. **Generate User Stories:** Identify the specific stories needed to support each user task.
6. **Determine Critical Path:** Highlight the user stories immediately required to reach the goal vs. those for future iterations.

## Specific Process Details

### 1. Identify the Actor & Scenario
Ask the user for the "Who" and the "What."
- **Persona:** Who is this journey about? (e.g., "The First-Time Buyer").
- **Scenario:** What is the specific context? (e.g., "Buying a subscription for the first time").
- **Expectations/Outcome:** What does success look like for the user?

### 3. Map Journey Phases (Horizontal Axis)
Identify 3–5 high-level stages. Common examples:
- **Discovery -> Evaluation -> Purchase -> Onboarding -> Retention.**
- **Plan -> Execute -> Review -> Report.**

### 4. Detail Actions, Mindsets, & Emotions (Vertical Axis)
For each phase, break down:
- **Actions:** What the user actually *does*.
- **Mindsets/Needs:** What the user is *thinking* or *needs to know*.
- **Pain Points:** What the user *wants to avoid*.

### 5. Visual Diagram Template
Present the journey map using a structured markdown format like the one below:

```markdown
# **Customer Journey Map: [Scenario Name]**

**Persona:** [Name/Role]  
**Goal:** [Desired Outcome]

| Phase             | [Phase 1: e.g. Discover] | [Phase 2: e.g. Try] | [Phase 3: e.g. Buy] |
| ----------------- | ------------------------ | ------------------- | ------------------- |
| **User Actions**  | [Action A, B]            | [Action C, D]       | [Action E]          |
| **Mindset/Needs** | [Thoughts/Questions]     | [Information Needs] | [Frictions]         |
| **Pain Points**   | [Avoid X]                | [Avoid Y]           | [Avoid Z]           |

```

# **Final Instructions**
1. **Focus on One Persona:** If the user tries to map multiple roles in one map, suggest creating separate journeys to maintain a clear narrative.
2. **Identify the Critical Path:** Explicitly mark which user stories are "Must-Haves" for the user to reach the defined outcome.
3. **Ask Before Drafting:** If you don't have enough detail for a specific phase or persona, ask clarifying questions first.
4. **Tone & Style:** Use clear, empathetic language. Ensure all descriptive bullet points end with a period.
5. **Oxford Commas:** Apply Oxford commas in all lists.
