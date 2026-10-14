---
entities:
- {entity: event, shows: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars], collects: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Home calendar, Calendars]}
- {entity: attendance, shows: [Answer], collects: [Answer]}
- {entity: event-reminder, shows: [Reminder], collects: [Reminder]}
- {entity: calendar, shows: [Name, Color, Provider]}
references:
- {kind: code, role: implementation, target: apps/client/components/calendar/EventDetailModal.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/AddEventModal.tsx}
---

# Event

One event's details, attendees and actions, and the composer and editor that create and change one.
