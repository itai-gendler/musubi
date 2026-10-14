---
appliesTo:
- {type: capability, id: change-task-status}
- {type: capability, id: edit-task}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#normalizeTaskPatch}
---

# Completing a task records when and finishes it

A task set to Completed records its completion time and is 100% done; moving it out of Completed clears the completion time.
