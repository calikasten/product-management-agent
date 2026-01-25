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
| Project Set Up             |    <- a centralized location to organize multiple chats and tasks in a dedicated space
├────────────────────────────┤
│ Model System Prompt        │
├────────────────────────────┤
│ Model Alignment & Training │
└────────────────────────────┘
```
These layers generally exist across different model providers and tools but are unique in their exact functinoality and nomenclature.
| <center>**Model Provider**</center> | <center>**Tool Name**</center> | <center>**Tool Format**</center> | <center>**Projects**</center> | <center>**Custom Tool**</center> | <center>**User Preferences**</center>            |
| ----------------------------------- | ------------------------------ | -------------------------------- | ----------------------------- | -------------------------------- | ------------------------------------------------ |
| Anthropic                           | Claude                         | UI                               | Projects                      |                                  | Settings > General > Personal Preferences        |
| Anthropic                           | Claude Code                    | CLI                              |                               | `SKILLS.md`                      | `CLAUDE.md`                                      |
| OpenAI                              | ChatGPT                        | UI                               | Projects                      | CustomGPTs                       | Settings > Personalization > Custom Instructions |
| OpenAI                              | Codex                          | CLI                              |                               | `SKILL.md`                       | `AGENTS.md`                                      |
| Google                              | Gemini                         | UI                               | NotebookLM                    | Gemini Gems                      | Settings > Instructions                          |
| Google                              | Gemini CLI                     | CLI                              |                               |                                  | `GEMINI.md`                                      |

## Cursor
[Cursor](https://cursor.com/) is my current tool of choice for allowing agents to take action on files within my projects directory and utilizing MCP servers, all while having a familiar IDE UI.
