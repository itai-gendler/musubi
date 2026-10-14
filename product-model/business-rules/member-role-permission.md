---
appliesTo:
- {type: entity, id: calendar-membership, effect: changes, facts: [Role]}
permits:
- related: [{verb: has, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is: Owner}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#setCalendarMemberRole}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#transferCalendarOwnership}
---

# Only the owner changes members' roles

The owner makes members editors or viewers, and hands the calendar over by making a member the owner. Nobody else changes a role.
