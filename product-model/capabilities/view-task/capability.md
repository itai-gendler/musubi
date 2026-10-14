---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/CalendarTaskDetails.tsx}
- {kind: code, role: implementation, target: apps/client/components/tasks/TaskDetailModal.tsx}
---

# View task

A user opens a task they can see: its notes, status, dates, priority, repeat, link, related task and the calendars it is in, with its home marked.
