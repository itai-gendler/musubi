---
entities:
- {entity: task, shows: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Related task, Completed at, Home calendar, Calendars], collects: [Title, Notes, Starts, Due, All day, Repeat, Link, Home calendar]}
- {entity: calendar, shows: [Name, Color, Provider, Supports tasks, Live task links]}
references:
- {kind: code, role: implementation, target: apps/client/components/tasks/TaskDetailModal.tsx}
- {kind: code, role: implementation, target: apps/client/components/tasks/TaskEditorModal.tsx}
---

# Task

One task's details, status, priority and actions, and the editor that creates or changes one.
