---
appliesTo:
- {type: entity, id: calendar-membership, effect: removes}
permits:
- related: [{verb: holds, entity: user}]
  when:
  - {fact: Role, is-not: Owner}
- related: [{verb: has, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is: Owner}
  - {fact: Role, is-not: Owner}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#removeCalendarMember}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerLeaveCalendar}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerKickMember}
---

# Members leave and the owner removes them, but the owner stays

A member who is not the owner leaves on their own; the owner removes any other member. The owner's own membership is never removed this way: they hand the calendar over or delete it.
