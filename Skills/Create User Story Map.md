---
name: create-user-story-map
description: Creates a visual user story map as a Mermaid diagram that organizes user activities, tasks, and stories to illustrate the user's journey and prioritize delivery.
---

# **Purpose**
This skill generates a user story map as a Mermaid diagram. A user story map visualizes the user's journey by organizing work into user activities (high-level goals), user tasks (steps to achieve those goals), and user stories (specific features or functionality). This helps teams understand the big picture, prioritize work, and ensure they're building the right things in the right order.

## When To Use
Use this skill when you need to:
- Break down a product or feature into a structured user journey
- Visualize how user stories relate to higher-level user activities and tasks
- Organize and prioritize work from a user-centric perspective
- Create a shared understanding of the user experience across the team

Do not use this skill when:
- You only need to split existing user stories into smaller pieces 
- You need detailed acceptance criteria or story specifications 
- You need to create Jira tickets

# **Overall Agent Process**
1. **Gather Context:** Check for existing documents (PRDs, customer journey maps, meeting notes) that describe the user journey or feature scope.
2. **Ask Clarifying Questions:** If context is incomplete, ask structured questions about user activities, tasks, and desired outcomes.
3. **Structure the Story Map:** Organize information into three levels: user activities (top level), user tasks (middle level), and user stories (bottom level).
4. **Generate Mermaid Diagram:** Create a visual Mermaid diagram that represents the user story map with clear hierarchy and relationships.

## Specific Process Details

### 1. Gather Context
First, check if the user has provided or referenced any existing documents such as:
- Product Requirements Documents (PRDs)
- Customer journey maps
- Feature specifications
- Meeting notes or brainstorming outputs

Read these documents to extract:
- The target user or persona
- The user's high-level goals (activities)
- The steps users take to achieve those goals (tasks)
- Specific features or functionality needed (stories)

### 2. Ask Clarifying Questions
If the existing context is insufficient, ask targeted questions to fill gaps:

**About User Activities (High-Level Goals):**
- "What are the main activities or goals the user is trying to accomplish?"
- "What is the user's primary objective when using this product/feature?"

**About User Tasks (Steps to Achieve Goals):**
- "What are the key steps or tasks the user needs to complete for each activity?"
- "In what order does the user typically perform these tasks?"

**About User Stories (Specific Features):**
- "What specific features or functionality does the user need to complete each task?"
- "Are there any must-have features versus nice-to-have features?"

**About Scope:**
- "Are there any constraints on scope or timeline that should influence prioritization?"
- "Which parts of the journey are most critical to the user's success?"

### 3. Structure the Story Map
Organize the information into a three-level hierarchy:

**Level 1 - User Activities:** High-level goals or outcomes the user wants to achieve. These are broad and outcome-focused (e.g., "Onboard to Platform," "Analyze Sales Data," "Share Insights").

**Level 2 - User Tasks:** Specific steps or tasks the user performs to accomplish each activity. These are action-oriented and sequential (e.g., "Create Account," "Import Data," "Generate Report").

**Level 3 - User Stories:** Individual features or functionality that support each task. These are concrete and deliverable (e.g., "Email verification," "CSV upload," "Export to PDF").

Ensure:
- Activities flow left to right in a logical sequence
- Tasks under each activity are ordered by typical user flow
- Stories under each task are grouped logically
- The map reads like a narrative of the user's journey

### 4. Generate Mermaid Diagram
Create a Mermaid diagram using the `graph TD` (top-down) format with the following structure:

```
graph TD
    %% User Activities (Level 1)
    A1[Activity 1]
    A2[Activity 2]
    A3[Activity 3]
    
    %% User Tasks (Level 2)
    A1 --> T1[Task 1.1]
    A1 --> T2[Task 1.2]
    A2 --> T3[Task 2.1]
    A2 --> T4[Task 2.2]
    A3 --> T5[Task 3.1]
    
    %% User Stories (Level 3)
    T1 --> S1[Story 1.1.1]
    T1 --> S2[Story 1.1.2]
    T2 --> S3[Story 1.2.1]
    T3 --> S4[Story 2.1.1]
    T3 --> S5[Story 2.1.2]
    T4 --> S6[Story 2.2.1]
    T5 --> S7[Story 3.1.1]
    
    %% Styling
    classDef activity fill:#e1f5ff,stroke:#0288d1,stroke-width:2px
    classDef task fill:#fff9c4,stroke:#f57f17,stroke-width:2px
    classDef story fill:#f3e5f5,stroke:#7b1fa2,stroke-width:1px
    
    class A1,A2,A3 activity
    class T1,T2,T3,T4,T5 task
    class S1,S2,S3,S4,S5,S6,S7 story
```

**Styling Guidelines:**
- User Activities: Blue background (`#e1f5ff`) with blue border
- User Tasks: Yellow background (`#fff9c4`) with orange border
- User Stories: Purple background (`#f3e5f5`) with purple border
- Use clear, concise labels (avoid overly long text in nodes)

# **Final Instructions**
1. Always start by checking for existing context documents before asking questions.
2. Ensure the story map flows logically from top to bottom following the user's journey.
3. Keep labels concise—use short phrases rather than full sentences.
4. Use consistent naming conventions (e.g., activities as outcomes, tasks as actions, stories as features).
5. If the map becomes too complex (more than 5 activities or 20+ stories), suggest breaking it into multiple focused maps.
6. Offer to iterate and refine the map based on user feedback.
