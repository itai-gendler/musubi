---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#normalizeTaskPatch}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/CalendarTaskDetails.tsx}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/tasks.tsx}
---

# Change task status

An owner or editor of a task's home calendar sets it to Needs action, In progress, Completed or Cancelled. Completing stamps when; anyone the task is shared with sees the same status.
