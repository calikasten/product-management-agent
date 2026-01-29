# Product Management Agent
Instructions and prompts for using an agent as an autonomous partner for product management work. Last Updated 01/28/2026. 

For more information on how to effectively use these prompt files and set up agents, see [LLM Context 101](https://github.com/calikasten/agents/blob/main/README.md#llm-context-101) and [Cursor Set Up](https://github.com/calikasten/agents/blob/main/README.md#cursor-setup).

## General Skills
AI skills that can be used across multiple tasks regardless of domain.

[Create New AI Skill](https://github.com/calikasten/product-management-agent/blob/main/Skills/Create%20New%20AI%20Skill.md) <br>
Generates a standardized SKILL.md file for a new AI skill by clarifying requirements, producing clear, agent-ready instructions, and saving it to the correct directory.

[Effective Writer](https://github.com/calikasten/product-management-agent/blob/main/Skills/Effective%20Writer.md) <br>
Creates or edits content to be concise, clear, and high-impact, preserving the user’s tone while optimizing for busy professionals, applying evidence-based writing principles and rigorous editing standards.

[Manage Task List](https://github.com/calikasten/product-management-agent/blob/main/Skills/Manage%20Task%20List.md) <br>
Maintains an up-to-date Markdown task list by adding, updating, reordering, and archiving tasks, tracking blockers and priorities, and generating clear progress summaries for fast visibility and informed decision-making.

[Provide Critical Feedback](https://github.com/calikasten/product-management-agent/blob/main/Skills/Provide%20Critical%20Feedback.md) <br>
Provides direct, evidence-based feedback on product ideas and artifacts by challenging assumptions, surfacing strategic gaps, and offering concrete guidance to strengthen product thinking, decision-making, and communication.

## Strategy & Planning

[Calculate TAM]

[Conduct Market Research]

[Create Now-Next-Later Roadmap](https://github.com/calikasten/product-management-agent/blob/main/Skills/Create%20Now-Next-Later%20Roadmap.md) <br>
Creates outcome-driven "Now, Next, Later" roadmaps that illustrate progress as predictions rather than rigid promises.

[Frame Problem Space]

[Lean Canvas Brainstorm](https://github.com/calikasten/product-management-agent/blob/main/Skills/Lean%20Canvas%20Brainstorm.md) <br>
Facilitates a structured Lean Canvas brainstorming session to deconstruct product ideas into actionable business models, identifying market demand, core problems, and unique value.

[Prioritization Brainstorm](https://github.com/calikasten/product-management-agent/blob/main/Skills/Prioritization%20Brainstorm.md) <br>
Facilitates a structured brainstorming session to prioritize problems, features, or tasks using prioritization frameworks.

[Strategy Brainstorm](https://github.com/calikasten/product-management-agent/tree/main/Skills) <br>
Acts as a strategic collaborator to pressure-test product ideas, identify market opportunities, and apply structured stratagic frameworks.

[Write OKRs](https://github.com/calikasten/product-management-agent/blob/main/Skills/Write%20OKRs.md) <br>
Drafts and refines high-impact, outcome-based Objectives and Key Results (OKRs) using leading indicators, North Star metrics, and growth frameworks to bridge the gap between vision and execution.

[Write Positioning Statement]

## Discovery & Validation

[Create Customer Journey Map](https://github.com/calikasten/product-management-agent/blob/main/Skills/Create%20Customer%20Journey%20Map.md) <br>
Visually diagrams the path a user takes to reach a goal, identifying core activities, tasks, and the critical user stories required for delivery.

[Create Jobs To Be Done]

[Create Market Validation Plan]

[Create Product Validation Plan]

[Customer Interview Prep]

[Discovery Brainstorm](https://github.com/calikasten/product-management-agent/blob/main/Skills/Discovery%20Brainstorm.md) <br>
Facilitates a structured product discovery session to validate market opportunities, define user problems, and chart paths to outcomes using discoverey frameworks.

## Product Definition

[Create Storyboard]

[Create User Story Map]

[Write PRD](https://github.com/calikasten/product-management-agent/blob/main/Skills/Write%20PRD.md) <br>
Creates an implementation-ready PRD (Product Requirements Document) by asking structured clarifying questions and organizing validated inputs into a clear, standardized PRD template.

## Execution & Delivery

[Create Jira Ticket](https://github.com/calikasten/product-management-agent/blob/main/Skills/Create%20Jira%20Ticket.md) <br>
Transforms prompts or meeting notes into clear, actionable Jira user stories and bug tickets through structured clarification and explicit acceptance criteria, ready for automated creation via the [Atlassian MCP server](https://www.atlassian.com/platform/remote-mcp-server).

[Split User Story](https://github.com/calikasten/product-management-agent/blob/main/Skills/Split%20User%20Story) <br>
Splits large or complex user stories into smaller, high-value units of work to reduce risk, increase visibility, and maintain a steady delivery cadence.

[Sprint Review Summary](https://github.com/calikasten/product-management-agent/blob/main/Skills/Sprint%20Review%20Summary.md) <br>
Summarizes weekly sprint progress by analyzing Jira tickets to highlight shipped work, blockers, in-progress items, and upcoming priorities.

[Write End of Life Announcement](https://github.com/calikasten/product-management-agent/blob/main/Skills/Write%20End%20Of%20Life%20Announcement.md) <br>
Creates clear, professional end-of-life announcements that inform users when an application or feature is being deprecated, including timelines, migration paths, and support information.

[Write Release Notes](https://github.com/calikasten/product-management-agent/blob/main/Skills/Write%20Release%20Notes.md) <br>
Creates clear, non-technical release notes by analyzing shipped Jira tickets and translating recent features and fixes into concise explanations of workflow changes and user benefits.

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

| **Model Provider** | **Tool Name** | **Tool Format** | **Projects** | **Custom Tool** | **User Preferences**                             |
| ------------------ | ------------- | --------------- | ------------ | --------------- | ------------------------------------------------ |
| Anthropic          | Claude        | UI              | Projects     |                 | Settings > General > Personal Preferences        |
| OpenAI             | ChatGPT       | UI              | Projects     | Custom GPTs     | Settings > Personalization > Custom Instructions |
| Google             | Gemini        | UI              | NotebookLM   | Gemini Gems     | Settings > Instructions                          |

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

| **Tool Name** | **Tool Format**     | **Project Representation** | **System-Level Instructions**           | **Task-Specific Instructions** | 
| ------------- | ------------------- | -------------------------- | --------------------------------------- | ------------------------------ |
| Claude Code   | CLI                 | Project folder             | `CLAUDE.md`                             | `SKILL.md`                     |
| Cursor        | IDE                 | Project folder             | Files in `.cursor/rules/`               | `SKILL.md`                     |
| Gemini CLI    | CLI                 | Project folder             | `GEMINI.md`                             | `SKILL.md`                     |
| Antigravity   | IDE                 | Project folder             | `GEMINI.md` (also supports `AGENTS.md`) | `SKILL.md`                     |
| Codex         | CLI / IDE extension | Project folder             | `AGENTS.md`                             | `SKILL.md`                     |

Skills can be utilized on a project level or on a global level:
| **Tool Name** | **Project Path**  | **Global Path**                 |
| ------------- | ----------------- | ------------------------------- |
| Claude Code   | `.claude/skills/` | `~/.claude/skills/`             |
| Cursor        | `.cursor/skills/` | `~/.cursor/skills/`             |
| Gemini CLI    |	`.gemini/skills/` |	`~/.gemini/skills/`             |
| Antigravity   | `.agent/skills/`  | `~/.gemini/antigravity/skills/` |
| Codex         | `.codex/skills/`  | `~/.codex/skills/`              |

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
Cursor rules control agent behavior within the codebase, similar to `AGENTS.md` files. Store rules in `.cursor/rules/` and create multiple files in `.md` or `.mdc` formats.

1. Create the `.cursor/rules` folders in your project.
2. Navigate to the `rules` folder:
```shell
cd /full/folder/path/for/project/.cursor/rules
```
3. Pull the latest version of the agent instructions prompt (`AGENTS.md`) from this repo and save it as a `.mdc` file:
```shell
 curl -s 'https://raw.githubusercontent.com/calikasten/product-management-agent/refs/heads/main/AGENTS.md' > './AGENTS.mdc'
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
 curl -s 'https://raw.githubusercontent.com/calikasten/product-management-agent/main/Skills/Writete%20PRD.md' > './SKILL.md'  
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
