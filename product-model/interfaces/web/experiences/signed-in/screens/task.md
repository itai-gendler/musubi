---
entities:
- {entity: task, shows: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Related task, Completed at, Home calendar, Calendars], collects: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Home calendar]}
- {entity: calendar, shows: [Name, Color, Provider, Supports tasks, Live task links]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/CalendarTaskDetails.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/TaskList.tsx}
---

# Task

One task: its details, its calendars with the home marked, and the editor that creates or changes it.
