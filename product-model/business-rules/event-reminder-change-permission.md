---
appliesTo:
- {type: entity, id: event-reminder, effect: changes}
permits:
- related: [{verb: sets, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/reminders.ts#handlerPutEventReminder}
---

# Only the person changes their own reminder for an event

An event's reminder choice belongs to one person and changes no one else's reminders.
