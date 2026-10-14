---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/TaskList.tsx}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/tasks.tsx}
- {kind: code, role: implementation, target: packages/db/src/queries/tasks.ts#getUserTasks}
---

# Browse tasks

A user sees every task they can see through their calendars, each once even when it is linked into several of them; on the web as a list or as a board with a column per status.
