---
appliesTo:
- {type: capability, id: remind-of-events}
- {type: capability, id: email-event-changes}
- {type: capability, id: answer-event}
references:
- {kind: code, role: implementation, target: packages/calendar/src/reminders.ts#resolveReminders}
- {kind: code, role: implementation, target: apps/api/src/event_notifications.ts#queueEventChange}
---

# Declined and cancelled events neither remind nor email

Nothing reminds a person of an event they declined, an event marked cancelled, or an occurrence whose reminder time has passed; declining also stops change emails about it.
