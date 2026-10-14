---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerRemoveTask}
- {kind: code, role: implementation, target: apps/client/components/tasks/TaskDetailModal.tsx}
---

# Remove task from calendar

A user takes a task out of one calendar that is not its home and that they edit. It stays in its home and other calendars.
