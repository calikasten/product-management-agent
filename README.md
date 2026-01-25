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
│ User Preferences           │    <- a set of unique personalization settings users can specify to instruct AI on how to communicate, behave, and respond
├────────────────────────────┤
│ Custom Tool                │    <- a reusable AI instance with context and reference knowledge for a domain-specific capability
├────────────────────────────┤
| Project                    |    <- a centralized location to organize multiple chats and tasks in a dedicated space
├────────────────────────────┤
│ Model System Prompt        │
├────────────────────────────┤
│ Model Alignment & Training │
└────────────────────────────┘
```
These layers generally exist across different model providers and tools but are unique in their exact functionality and nomenclature.
| <center>**Model Provider**</center> | <center>**Tool Name**</center> | <center>**Tool Format**</center> | <center>**Projects**</center> | <center>**Custom Tool**</center> | <center>**User Preferences**</center>            |
| ----------------------------------- | ------------------------------ | -------------------------------- | ----------------------------- | -------------------------------- | ------------------------------------------------ |
| Anthropic                           | Claude                         | UI                               | Projects                      |                                  | Settings > General > Personal Preferences        |
| OpenAI                              | ChatGPT                        | UI                               | Projects                      | CustomGPTs                       | Settings > Personalization > Custom Instructions |
| Google                              | Gemini                         | UI                               | NotebookLM                    | Gemini Gems                      | Settings > Instructions                          |

Where available, custom tools and projects can be used in conjunction with each other. Projects operate as the top-level "folder" that handles collaboration, resource sharing, and workflow organization. Custom tools can then be used inside a project, inheriting the shared resources and configuration of the project while still functioning as reusable assistants, each with its own instructions and task focus. 
```
┌─────────────────────────────────────────────────┐
│ Project                                         |
| (Containis shared context and resources)        │
│  ┌───────────────────┐   ┌───────────────────┐  │
│  │ Custom Tool 1     │   │ Custom Tool 2     │  │
│  │ - Prompt          │   │ - Prompt          │  │
│  │ - Tools / Data    │   │ - Tools / Data    │  │
│  │ - Behavior        │   │ - Behavior        │  │
│  └───────────────────┘   └───────────────────┘  │
└─────────────────────────────────────────────────┘
```

## Providing Context Via File Directories
While projects and custom tools are commonly referenced through web, desktop, or mobile UIs, agents invoked from the CLI or IDE can instead derive context directly from an exposed project directory. To enable LLMs to effective interact with the project directory, specific files should be included to define how agents should navigate, interpret, and interact with the project directory. Similar to the varition in nomenclature for projects and custom tools, the folder structure setup and exact file names vary.
| <center>**Model Provider**</center> | <center>**Tool Name**</center> | <center>**Tool Format**</center> | <center>**Projects**</center> | <center>**Custom Tool**</center> | <center>**User Preferences**</center>            |
| ----------------------------------- | ------------------------------ | -------------------------------- | ----------------------------- | -------------------------------- | ------------------------------------------------ |
| Anthropic                           | Claude Code                    | CLI                              | File Directory               | `SKILLS.md`                      | `CLAUDE.md`                                      |
| OpenAI                              | Codex                          | CLI/IDE Extension                | File Directory               | `SKILL.md`                       | `AGENTS.md`                                      |
| Google                              | Gemini CLI                     | CLI                              | File Directory               |                                  | `GEMINI.md`                                      |
| Google                              | Antigravity                    | IDE                              | File Directory               |                                  | `GEMINI.md` (also supports `AGENTS.md`   |
| Cursor                              | Cursor                         | IDE                              | File Directory               | `.cursor/skills/skill-name/SKILL.md` Folder | `.cursor/rules` Folder                |

### Cursor
[Cursor](https://cursor.com/) is my current tool of choice for allowing agents to take action on files within my projects directory and utilizing MCP servers, all while having a familiar IDE UI.
