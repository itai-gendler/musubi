---
entities:
- {entity: event, shows: [Title, Starts, Ends, All day, Color]}
- {entity: task, shows: [Title, Status, Due]}
- {entity: calendar, shows: [Name, Color]}
references:
- {kind: code, role: implementation, target: apps/client/app/(tabs)/index.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/AgendaView.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/CalendarFilterBar.tsx}
---

# Home

The calendar: month, week and day views and the agenda, with a filter bar of calendars and the composer docked at the bottom.
