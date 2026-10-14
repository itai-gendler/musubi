---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerUpdateTask}
---

# Edit task

An owner or editor of a task's home calendar changes its content. Editing rights on another calendar it is linked into are not enough.
