---
appliesTo:
- {type: entity, id: event, effect: changes, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance]}
permits:
- related: [{verb: homes, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
- related: [{verb: homes, entity: calendar}, {verb: mirrors, entity: connected-account}, {verb: connects, entity: user}]
- unattended: true
references:
- {kind: code, role: implementation, target: apps/api/src/permissions.ts#assertCanEditEvent}
- {kind: code, role: implementation, target: apps/api/src/event_permissions.ts#assertEventContentAccess}
---

# Only owners and editors of its home calendar change an event

An event's content changes through its home calendar alone: editing rights on another calendar it is linked into are not enough, whatever calendar it is looked at from. In a synced home calendar the person whose account it comes from may also change it, leaving it to the provider to accept or refuse. Musubi itself applies the changes it brings in from providers.
