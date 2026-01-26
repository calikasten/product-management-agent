# Agents & Skills
Instructions and prompts for using LLMs as autonomous agents. Last Updated 01/25/2026. 

For more information on how to effectively use these prompt files and set up agents, see [LLM Context 101](https://github.com/calikasten/agents/blob/main/README.md#llm-context-101) and [Cursor Set Up](https://github.com/calikasten/agents/blob/main/README.md#cursor-setup).

---
## Agents
[Effective Writer](https://github.com/calikasten/agent-skills/blob/main/Agents/Effective%20Writer.md) <br>
Agent instructions for producing written material that is concise, clear, and readable with context on avoiding AI writing patterns and maintaining the user's natural tone of voice.

[Product Manager](https://github.com/calikasten/agent-skills/blob/main/Agents/Product%20Manager.md) <br>
Agent instructions for completing basic Product Management tasks grounded in context on product strategy and discovery, agile methodology, and go-to-market best practices.

## Product Manager Skills
[Create Jira Ticket](https://github.com/calikasten/agent-skills/blob/main/Skills/Create%20Jira%20Ticket.md) <br>
Transforms prompts or meeting notes into clear, actionable Jira user stories and bug tickets through structured clarification and explicit acceptance criteria, ready for automated creation via the [Atlassian MCP server](https://www.atlassian.com/platform/remote-mcp-server).

[Create PRD](https://github.com/calikasten/agent-skills/blob/main/Skills/Create%20PRD.md) <Br>
Creates an implementation-ready PRD (Product Requirements Document) by asking structured clarifying questions and organizing validated inputs into a clear, standardized PRD template.

[Provide Critical Feedback](https://github.com/calikasten/agent-skills/blob/main/Skills/Provide%20Critical%20Feedback.md) <br>
Provides direct, evidence-based feedback on product ideas and artifacts by challenging assumptions, surfacing strategic gaps, and offering concrete guidance to strengthen product thinking, decision-making, and communication.

---
# LLM Context 101
An AI model's context can be compared to a layer cake, where higher layers can *add* behavior, but usually *cannot override* lower layers.

```
┌────────────────────────────┐
│ Current User Prompt        │
├────────────────────────────┤
│ Chat History               │
├────────────────────────────┤
│ User Preferences           │    ← personalization settings that instruct the AI how to communicate, behave, and respond
├────────────────────────────┤
│ Custom Tool                │    ← a reusable, named AI configuration with scoped context, tools, and instructions
├────────────────────────────┤
│ Project                    │    ← a centralized space to organize multiple chats, tasks, and shared resources
├────────────────────────────┤
│ Model System Prompt        │    ← global instructions that define the AI's role and rules across all interactions
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
| Claude Code   | CLI             | Project folder             | `CLAUDE.md`                   | `SKILL.md`                     |
| Cursor        | IDE             | Project folder             | Files in `.cursor/rules/`     | `SKILL.md`                     |
| Gemini CLI    | CLI             | Project folder             | `GEMINI.md`                   | `SKILL.md`                     |
| Antigravity   | IDE             | Project folder             | `GEMINI.md` (also supports `AGENTS.md`) | `SKILL.md`           |
| Codex         | CLI / IDE extension | Project folder         | `AGENTS.md`                   | `SKILL.md`                     |

Skills can be utilized on a project level or on a global level:
| **Tool Name** | **Project Path** | **Global Path** |
| ------------- | ---------------- | --------------- |
| Claude Code   | `.claude/skills/` | `~/.claude/skills/` |
| Cursor        | `.cursor/skills/` | `~/.cursor/skills/` |
| Gemini CLI    |	`.gemini/skills/` |	`~/.gemini/skills/` |
| Antigravity   | `.agent/skills/`  | `~/.gemini/antigravity/skills/` |
| Codex         | `.codex/skills/`  | `~/.codex/skills/` |

Each skill resides in its own subdirectory under `.cursor/skills/` and contains a `SKILL.md` file:
```
skills/
├── my-skill/                       
│  ├── SKILL.md                       ← (required) instructions and metadata
│  └── scripts/                       ← (optional) executable scripts/tools
│     └── script-name.sh              
│  └── references/                    ← (optional) static documentation and examples
│  └── assets/                        ← (optional) templates and binary resources
```

---
# Cursor Setup
[Cursor](https://cursor.com/) is currently my preferred tool for its filesystem-based customization, built-in MCP server integration, and familiar IDE interface. To use the agent instructions and skills from this GitHub repo, follow these steps to pull the latest agent or skill files and create symlinks to reference additional context in your Cursor project.

## Setting Up Cursor Rules
Cursor rules control agent behavior within the codebase, similar to AGENTS.md files. Store rules in .cursor/rules/ and create multiple files in `.md` or `.mdc` formats.

1. Create the `.cursor/rules` folders in your project.
2. Navigate to the `rules` folder:
```shell
cd /full/folder/path/for/project/.cursor/rules
```
3. Pull the latest version of a prompt from this repo and save it as a `.mdc` file:
```shell
 curl -s 'https://raw.githubusercontent.com/calikasten/agent-skills/main/Agents/Effective%20Writer.md' > './effective-writer.mdc'
```

## Setting Up Cursor Skills
Cursor skills are step-by-step guides that teach agents specific tasks. 

1. Create the `.cursor/skills/` folders and a subdirectory for the skill.
2. Navigate to the specific skill folder:
```shell
cd /full/folder/path/for/project/.cursor/skills/specific-skill-name
```
3. Pull the latest version of a skill from this repo:
```shell
 curl -s 'https://raw.githubusercontent.com/calikasten/agent-skills/main/Skills/Create%20PRD.md' > './SKILL.md'  
```
## Setting Up Additional Context
Additional contextcan be provided to Cursor by by linking other files or folders in your project. Use symlinks to point to the original location so updates are automatically reflected.

1. Navigate to the project folder:
```shell
cd /full/folder/path/for/project
```
2. Copy the full path of the file or folder to reference.
3. Create a symbolic link pointing to the reference file/folder:
```shell
ln -s /full/file/path/to/context/folder ./folder-name
```
