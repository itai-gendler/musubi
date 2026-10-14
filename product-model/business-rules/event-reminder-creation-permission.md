---
appliesTo:
- {type: entity, id: event-reminder, effect: creates}
permits:
- related: [{verb: sets, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/reminders.ts#handlerPutEventReminder}
---

# Only the person sets their own reminder for an event

An event's reminder choice belongs to one person and changes no one else's reminders.
