---
appliesTo:
- {type: entity, id: attendance, effect: changes}
permits:
- related: [{verb: gives, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerSetAttendance}
---

# Only the person changes their own answer

Anyone who can see an event that allows attendance answers for themselves; nobody answers for someone else.
