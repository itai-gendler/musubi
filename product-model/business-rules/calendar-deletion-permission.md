---
appliesTo:
- {type: entity, id: calendar, effect: removes}
permits:
- related: [{verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is: Owner}
  - {fact: Personal, is: false}
- related: [{verb: mirrors, entity: connected-account}, {verb: connects, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerRemoveCalendar}
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts#handlerDisconnectExternalCalendar}
- {kind: code, role: implementation, target: packages/types/src/permissions.ts#can}
---

# Only the owner deletes a calendar, and never a personal one

The owner deletes a calendar that is not their personal calendar. The person whose connected account a synced calendar comes from may also stop syncing it, which takes it out of Musubi even when the provider shows it to them read-only.
