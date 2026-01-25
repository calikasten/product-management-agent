# Agents
Instructions and prompts for using LLMs. Last Updated 01/25/2026.

## LLM Context 101
An AI model's context can be compared to a layer cake, where higher layers can *add* behavior, but usually *cannot override* lower layers.

```
┌────────────────────────────┐
│ Current User Prompt        │
├────────────────────────────┤
│ Chat History               │
├────────────────────────────┤
│ User Preferences           │    <- personalization settings that instruct the AI how to communicate, behave, and respond
├────────────────────────────┤
│ Custom Tool                │    <- a reusable, named AI configuration with scoped context, tools, and instructions
├────────────────────────────┤
│ Project                    │    <- a centralized space to organize multiple chats, tasks, and shared resources
├────────────────────────────┤
│ Model System Prompt        │    <- global instructions that define the AI's role and rules across all interactions
├────────────────────────────┤
│ Model Alignment & Training │
└────────────────────────────┘
```

These layers generally exist across different model providers and tools, though their exact behavior and naming vary.

| **Model Provider** | **Tool Name** | **Tool Format** | **Projects** | **Custom Tool** | **User Preferences** |
| ------------------ | ------------- | --------------- | ------------ | --------------- | -------------------- |
| Anthropic          | Claude        | UI              | Projects     |                 | Settings > General > Personal Preferences |
| OpenAI             | ChatGPT       | UI              | Projects     | Custom GPTs     | Settings > Personalization > Custom Instructions |
| Google             | Gemini        | UI              | NotebookLM   | Gemini Gems     | Settings > Instructions |

Where available, custom tools and projects can be used together. Projects act as the top-level container for collaboration, shared context, and workflow organization. Custom tools then operate within a project, inheriting shared resources and configuration while remaining reusable assistants with their own prompts, tools, and task focus.

```
┌─────────────────────────────────────────────────┐
│ Project                                         │
│ (Contains shared context and resources)         │
│  ┌───────────────────┐   ┌───────────────────┐  │
│  │ Custom Tool 1     │   │ Custom Tool 2     │  │
│  │ - Prompt          │   │ - Prompt          │  │
│  │ - Tools / Data    │   │ - Tools / Data    │  │
│  │ - Behavior        │   │ - Behavior        │  │
│  └───────────────────┘   └───────────────────┘  │
└─────────────────────────────────────────────────┘
```

## Providing Context Via File Directories
Providing context via projects, custom tools, and user preferences is primarily done through web, desktop, or mobile apps with dedicated UIs. In contrast, agents invoked from the CLI or IDE derive context directly from an exposed project directory.

To enable LLMs to effectively interact with a project directory, specific files are used to define how agents should navigate, interpret, and operate within that directory.

In practice, UI-based context concepts map to filesystem-based equivalents as follows:
- **Projects** → Project directory
- **Custom Tools** → Task-specific instructions

A key difference is that while user preferences shape the interaction experience, CLI and IDE workflows are governed by documents that define system-level constraints and operating rules for the agent. This pattern exists across tools, though implementations and file naming conventions vary.

| **Tool Name** | **Tool Format** | **Project Representation** | **System-Level Instructions** | **Task-Specific Instructions** |
| ------------- | --------------- | -------------------------- | ----------------------------- | ------------------------------ |
| Claude Code   | CLI             | Project folder             | `CLAUDE.md`                   | `SKILLS.md` |
| Gemini CLI    | CLI             | Project folder             | `GEMINI.md`                   | `.gemini/skills/` folder |
| Cursor        | IDE             | Project folder             | Files in `.cursor/rules/`     | `.cursor/skills/<skill-name>/SKILL.md` |
| Antigravity   | IDE             | Project folder             | `GEMINI.md` (also supports `AGENTS.md`) | `.agent/skills/<skill-name>/SKILL.md` |
| Codex         | CLI / IDE extension | Project folder             | `AGENTS.md`                   | `SKILL.md` |

### Instruction Files
Certain files provide structured context that explains how to navigate and interact with the project directory.

- **AGENTS.md** files define how an agent should interpret the project directory and its contents.
- **SKILLS.md** files provide step-by-step instructions for completing specific tasks within that project.

