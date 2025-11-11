---
description: Read and summarize the current NOW.md file for instant project reorientation
mode: ask
---

# NOW.md Status

Read and summarize the current NOW.md file to provide instant project reorientation. Do NOT modify the file or run git commands.

## Instructions

1. **Read NOW.md** from the repository root (${workspaceFolder}/NOW.md)
   - If NOW.md doesn't exist, inform the user and suggest running `/now-update` to create it

2. **Provide a concise summary** in this format:

```
Project Status from NOW.md (last updated: <date>)

CURRENT FOCUS
<current_focus field>

BLOCKERS
<blocked_by field>

NEXT TASK
<immediate_task.intent>
Done when: <immediate_task.done_when>
Status: <immediate_task.status>

TESTS
Unit: <unit test status> | Integration: <integration test status>

KEY CONTEXT
<List key_decisions if any exist>
```

## Constraints

- Do NOT run git log, git status, or any other git commands
- Do NOT modify the NOW.md file
- Do NOT analyze the codebase beyond reading NOW.md
- Do NOT make inferences beyond what's in NOW.md
- Do NOT use emojis in the output
- Keep response under 200 words - this is for quick reorientation, not deep analysis

## Error Handling

- If NOW.md doesn't exist: "No NOW.md file found. Run `/now-update` to create one."
- If NOW.md is malformed: Present what can be read and note parsing issues
