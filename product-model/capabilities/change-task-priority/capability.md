---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/CalendarTaskDetails.tsx}
- {kind: code, role: implementation, target: apps/client/components/tasks/TaskDetailModal.tsx}
---

# Change task priority

An owner or editor of a task's home calendar sets its priority to none, high, medium or low.
