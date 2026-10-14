---
entities:
- {entity: event, shows: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars], collects: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Home calendar, Calendars]}
- {entity: attendance, shows: [Answer], collects: [Answer]}
- {entity: event-reminder, shows: [Reminder], collects: [Reminder]}
- {entity: calendar, shows: [Name, Color, Provider]}
entryPoints:
- {web: '/app/p/{page}/{view}/event/{event}'}
- {web: '/app/p/{page}/{view}/event/new'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventDetailsPopover.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventEditorForm.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/QuickCreate.tsx}
---

# Event

One event: its details, answers and reminder, the editor that changes it and the composer that creates one. Opened from the calendar, search or a notification.
