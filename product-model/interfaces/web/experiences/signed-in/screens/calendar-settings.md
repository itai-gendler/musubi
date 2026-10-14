---
entities:
- {entity: calendar, shows: [Name, Color, Provider], collects: [Name, Color]}
- {entity: calendar-membership, shows: [Reminder], collects: [Reminder]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/calendar-dialogs.tsx}
---

# Calendar settings

One calendar's name, colour and the user's own reminder rule for it, with deleting it or, for a synced calendar, stopping its sync.
