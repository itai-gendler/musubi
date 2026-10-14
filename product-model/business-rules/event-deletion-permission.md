---
appliesTo:
- {type: entity, id: event, effect: removes}
permits:
- related: [{verb: homes, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
- related: [{verb: homes, entity: calendar}, {verb: mirrors, entity: connected-account}, {verb: connects, entity: user}]
- unattended: true
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerRemoveEvent}
---

# Only owners and editors of its home calendar delete an event everywhere

Deleting an event from every calendar needs editing rights on its home, or being the person whose account a synced home calendar comes from, the provider having the last word. Musubi itself removes events deleted at their provider.
