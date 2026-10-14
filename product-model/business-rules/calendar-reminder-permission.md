---
appliesTo:
- {type: entity, id: calendar-membership, effect: changes, facts: [Reminder]}
permits:
- related: [{verb: holds, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/reminders.ts#handlerPutCalendarReminder}
---

# Only the member sets their own reminder rule for a calendar

A calendar reminder rule lives on the member's own membership; any member, viewers included, sets theirs, and nobody sets another's.
