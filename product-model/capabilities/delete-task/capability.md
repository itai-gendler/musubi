---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerRemoveTask}
---

# Delete task

An owner or editor of a task's home calendar deletes it everywhere it is linked; deletions are queued for its copies at providers.
