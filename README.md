# Agents
Instructions and prompts for using LLMs. Last Updated 01/25/2026.

## Agents

## Product Management Skills

---
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

A key difference is that while user preferences shape the interaction experience, CLI and IDE workflows are governed by documents that define system-level constraints and operating rules for the agent. Certain files provide structured context that explains how to navigate and interact with the project directory:

- **`AGENTS.md`** files define how an agent should interpret the project directory and its contents.
- **`SKILLS.md`** files provide step-by-step instructions for completing specific tasks within that project.

This pattern exists across tools, though implementations and file naming conventions vary.

| **Tool Name** | **Tool Format** | **Project Representation** | **System-Level Instructions** | **Task-Specific Instructions** |
| ------------- | --------------- | -------------------------- | ----------------------------- | ------------------------------ |
| Claude Code   | CLI             | Project folder             | `CLAUDE.md`                   | `SKILLS.md` |
| Gemini CLI    | CLI             | Project folder             | `GEMINI.md`                   | `.gemini/skills/` folder |
| Cursor        | IDE             | Project folder             | Files in `.cursor/rules/`     | `.cursor/skills/<skill-name>/SKILL.md` |
| Antigravity   | IDE             | Project folder             | `GEMINI.md` (also supports `AGENTS.md`) | `.agent/skills/<skill-name>/SKILL.md` |
| Codex         | CLI / IDE extension | Project folder             | `AGENTS.md`                   | `SKILL.md` |

## Cursor Setup
[Cursor](https://cursor.com/) is currently my preferred tool because of its filesystem-based customization, built-in MCP server integration, and familiar IDE interface. To use the agent instructions and skills stored in this GitHub repo, follow these steps to create symlinks to these files within a Cursor project.

*Note: Symlinks act as pointers to the original files, ensuring that any updates made while interacting with the files in Cursor automatically sync back to the repo, which remains the source of truth.*

### Cursor Rules
In Cursor, rules control agent behavior within the codebase, functioning like `AGENTS.md` files. Rules are stored in the `.cursor/rules/` folder. This folder can hold multiple rule files, named as you like, in either .md or .mdc formats.

1. Copy the full folder path name for the selected Cursor project folder to the clipboard as a text string
2. Navigate to the selected project folder:
```Shell
cd /'full folder path name for project'
```
3. Create a `.cursor/rules` folder:
```Shell
mkdir -p .cursor/rules
```
4. Navigate to the `rules` folder:
```Shell
cd .cursor/rules
```
5. Copy the full file path name for the agent file from Github (pull latest from Github)
6. Create symlink pointing at agent file:
```Shell
ln -s 'full file path name' ./'agent file name'
```
7. Navigate to Cursor and confirm new folders for `.cursor/` and `/rules` folders exist in project directory and `.cursor/rules/` contains `agent file name.md` file

### Cursor Skills
