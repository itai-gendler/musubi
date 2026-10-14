---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerLinkTask}
- {kind: code, role: implementation, target: packages/types/src/calendar.ts#calendarSupportsTaskLinks}
---

# Link task

A user who can see a task links it live into another calendar they edit. It stays one task with one status and home; Microsoft To Do lists take only independent copies.
