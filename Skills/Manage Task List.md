---
name: manage-task-list
description: Maintains an up-to-date Markdown task list by adding, updating, reordering, and archiving tasks, tracking blockers and priorities, and generating clear progress summaries for fast visibility and informed decision-making.
---

# **Purpose**
Maintains an accurate, up-to-date Markdown task list by adding, updating, reordering, and archiving tasks, tracking blockers and priorities, and generating clear progress summaries for fast visibility and informed decision-making.

## When To Use
Use this skill when the user wants to manage a task list (add tasks, update status, reorder priorities, archive completed items, or generate progress reports). Do not use this skill for tasks that don't involve task list management, or when the user wants to manage tasks in a different format or system.

# **Overall Agent Process**
Steps 1-4 can be conducted in any order to support the overall maintenance of the task list.

1. **Add New Tasks:** Create a new task based on the received input.
2. **Update Existing Tasks:** Indicate the status of a task including the date it was completed.
3. **Move Tasks:** Archive completed tasks and remove tasks that are no longer relevant.
4. **Reorder Tasks:** Change the order of tasks based on updated prioritization.
5. **Save Updated Task List:** Save the changes made to the task list file.
6. **Provide Pogress Report:** Write a summary of tasks completed, what's still blocked, and what's up next.

## Specific Process Details
### 1. Add New Tasks
The description of the task will either be provided initially, or a specific file containing meeting notes will be included in the initial prompt. If meeting notes are referenced, review the action items and create corresponding tasks based on the action item descriptions.

### 2. Update Existing Tasks
Update the task list:
- When starting a new task
- When completing a task
- When discovering new tasks
- When tasks are blocked
- When priorities change

Use clear, consistent status markers:
- `[ ]` Not started
- `[-]` Blocked
- `[x]` Complete

### 3. Move Tasks
Move completed tasks to the "Completed" section of the task list, with completed tasks grouped by date, e.g:
* January 1, 2026
- [x] Do laundry
- [x] Take out garbage

If instructed that a task is no longer relevant, remove it from the task list. Before deleting any tasks, ask the user if this is the task that should be removed and wait for user approval before proceeding.

### 4. Reorder Tasks
If instructed that a certain task is urgent or high priority, move that task to the top of the list. Make sure to keep any blocked tasks visible, group related tasks together, and maintain dependency order if relevant.

### 5. Save Updated Task List
- **Format:** markdown (`.md`)

### 6. Provide Pogress Report
If asked for a progress report, provide a summary of tasks completed so far that week (unless a different timeframe is specified) and what the next 3 priority tasks are and any blocked tasks. Follow this exact summary template:

```markdown
**Completed:**
- [Task 1]
- [Task 2]

**Blocked:**
- [Blocked task] - [Blocker reason]

**Up Next:**
- [Next task to tackle]
```

Be sure to call attention to newly blocked tasks or dependencies holding up progress, and tasks that seem to be taking longer than expected (based on when the task was added and your understanding of what the task is/the complexity of accomplishing the task).

### Best Practices
1. **Be Accurate**
	- Don't mark tasks complete unless they're truly done
	- Update status in real-time, not batch at end
	- Be honest about blockers and delays
	- Keep estimates realistic
2. **Be Detailed**
	- Explain blockers clearly
	- Document decisions made
	- Track open questions
3. **Be Organized**
	- Keep the list clean and readable
	- Use consistent formatting
	- Group related tasks
4. **Be Proactive**
	- Update the user on progress regularly
	- Flag issues immediately
	- Ask for direction when priorities are unclear
	- Celebrate completed milestones

# **Final Instructions**
1. Update status as soon as it changes.
2. Be transparent about progress and blockers.
3. Keep the task list as the source of truth.
4. Don't let the list get stale.
5. Make it easy to understand at a glance.
