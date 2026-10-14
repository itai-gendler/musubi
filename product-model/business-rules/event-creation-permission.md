---
appliesTo:
- {type: entity, id: event, effect: creates}
permits:
- related: [{verb: homes, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
- related: [{verb: homes, entity: calendar}, {verb: mirrors, entity: connected-account}, {verb: connects, entity: user}]
- unattended: true
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerCreateEvent}
- {kind: code, role: implementation, target: apps/api/src/event_permissions.ts#hasEventCalendarAccess}
---

# Owners and editors of its home create an event

An event is created by an owner or editor of the calendar that becomes its home, and of every other calendar it goes into. In a synced calendar the person whose account it comes from may also create one even where they hold Viewer, leaving it to the provider to accept or refuse. Musubi itself creates the events it brings in from providers.
