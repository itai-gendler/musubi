---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/reminders.ts#handlerPutEventReminder}
- {kind: code, role: implementation, target: apps/api/src/handlers/reminders.ts#handlerDeleteEventReminder}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventDetailsPopover.tsx}
---

# Change event reminder

A user chooses when one event reminds them, never included, or goes back to what it would inherit from their calendar rule or default. It changes nobody else's reminders.
