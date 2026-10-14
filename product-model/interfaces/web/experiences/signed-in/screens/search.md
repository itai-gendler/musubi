---
entities:
- {entity: event, shows: [Title, Starts, Calendars]}
- {entity: task, shows: [Title, Due, Status]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/SearchDialog.tsx}
---

# Search

Finding events and tasks across every calendar and date the user can see.
