---
appliesTo:
- {type: entity, id: calendar, effect: changes}
permits:
- related: [{verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is: Owner}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerUpdateCalendar}
- {kind: code, role: implementation, target: packages/types/src/permissions.ts#can}
---

# Only the owner changes a calendar

Renaming, recolouring and handing over a calendar are for its owner alone; editors and viewers cannot. For a synced calendar the owner is the person whose account it comes from.
