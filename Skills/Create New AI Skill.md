---
name: create-new-ai-skill   
description: Generates a standardized SKILL.md file for a new AI skill by clarifying requirements, producing clear, agent-ready instructions, and saving it to the correct directory.
---

# **Purpose**
This skill creates SKILL.md files for new AI skills. It gathers requirements through clarifying questions, writes clear and actionable instructions that agents can understand and implement, and saves the file to the proper directory.

## When To Use
Use this skill when the user wants to create a new AI skill with a standardized `SKILL.md` format. Do not use this skill for tasks that don't involve AI skill creation, or when the user explicitly wants to update an existing skill.

# **Overall Agent Process**
1. **Receive Initial Prompt:** The user provides a brief description of the new AI skill.
2. **Ask Clarifying Questions:** Before writing the `SKILL.md` file, the AI should ask clarifying questions to gather sufficient detail that the agent will need to know in order to implement the skill.
3. **Write Skill File:** Based on the initial prompt and the user's answers to the clarifying questions, write the SKILL.md file.
4. **Save Skill File:** Save the generated `SKILL.md` file in the proper directory.

## Specific Process Details
### 2. Ask Clarifying Questions
If any jargon in the initial prompt or description is confusing or unclear, ask clarifying questions. 

### 3. Write SKILL.md File
The primary reader is agents so requirements should be explicit, unambiguous, and avoid jargon where possible; make sure to provide enough detail for them to understand the skill's purpose and core logic. Your final output should follow this exact template:

```markdown
---
name: [Skill Name]
description: [Brief description of what this skill is and why it matters.]
---
# **Purpose**
[1–2 sentence description of what this skill does and when it should be used.]

## When To Use
[Clear conditions for invocation and explicit boundaries for when the skill should not be used.]

# **Overall Agent Process**
1. [Numbered list of steps the agent should follow when implementing the skill following this format: `1. **Example:** Description of step.`]

## Specific Process Details
### [Step Number and Step Name]
[Detailed instructions for the agent to follow when implementing the skill.]

# **Final Instructions**
1. [Final instructions for the agent to follow when implementing the skill]
```

### 4. Save SKILL.md File
Create a new directory within `.cursor/skills/` for [skill-name-in-kebab-case] and save the generated document as `SKILL.md`.

# **Final Instructions**
1. Ask clarifying questions if context is missing
