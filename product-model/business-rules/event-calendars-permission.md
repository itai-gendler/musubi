---
appliesTo:
- {type: entity, id: event, effect: changes, facts: [Calendars]}
permits:
- related: [{verb: lists, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerLinkEvent}
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerRemoveEvent}
---

# Owners and editors of a calendar link events into it and out of it

Linking an event into a calendar, or taking it out of one, needs the right to see the event and editing rights on that calendar; it does not need rights on the event's home.
