---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerForkTask}
---

# Copy task

A user makes an independent copy of a task they can see in another calendar they edit. The copy has its own home, status and future changes.
