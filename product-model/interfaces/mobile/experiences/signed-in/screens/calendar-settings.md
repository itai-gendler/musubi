---
entities:
- {entity: calendar, shows: [Name, Color, Provider], collects: [Name, Color]}
- {entity: calendar-membership, shows: [Role, Reminder], collects: [Reminder]}
references:
- {kind: code, role: implementation, target: apps/client/components/calendar/CalendarSettingsModal.tsx}
---

# Calendar settings

One calendar's actions and the user's own reminder rule for it.
