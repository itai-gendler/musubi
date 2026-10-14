---
entities:
- {entity: event, shows: [Title, Starts, Ends, All day, Color, Location]}
- {entity: task, shows: [Title, Status, Due]}
- {entity: calendar, shows: [Name, Color, Provider]}
- {entity: page, shows: [Name, Icon, View, Position, Default]}
entryPoints:
- {web: '/app/p/{page}/{view}?date={date}'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/app/p.$pageId.$view.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/Workspace.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/Sidebar.tsx}
---

# Calendar

The open page in its view — day, week, several weeks, month or agenda — with its events and dated tasks, the list of pages and the calendars that can be shown or hidden.
