---
entities:
- {entity: calendar, shows: [Name, Color, Provider], collects: [Name, Color]}
- {entity: connected-account, shows: [Provider, Account name]}
references:
- {kind: code, role: implementation, target: apps/client/app/(tabs)/calendars.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/CreateCalendarModal.tsx}
---

# Calendars

The user's calendars in their order, with creating, importing and syncing calendars.
