---
entities:
- {entity: task, shows: [Title, Status, Due, Priority, Repeat, Home calendar]}
entryPoints:
- {web: '/app/p/{page}/tasks?taskLayout={list|kanban}'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/TaskList.tsx}
---

# Tasks

Every task the user can see, once each, as a list or as a board with a column per status.
