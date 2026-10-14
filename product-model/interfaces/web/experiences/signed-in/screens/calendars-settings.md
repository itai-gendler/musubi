---
entities:
- {entity: calendar, shows: [Name, Color, Personal, Provider], collects: [Name, Color]}
- {entity: connected-account, shows: [Provider, Account name]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/CalendarsPanel.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/calendar-dialogs.tsx}
---

# Calendars settings

The user's calendars, with creating a calendar, importing an .ics file and exporting one.
