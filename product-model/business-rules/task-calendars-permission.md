---
appliesTo:
- {type: entity, id: task, effect: changes, facts: [Calendars]}
permits:
- related: [{verb: lists, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerLinkTask}
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerRemoveTask}
---

# Owners and editors of a calendar link tasks into it and out of it

Linking a task into a calendar, or taking it out of one that is not its home, needs the right to see the task and editing rights on that calendar.
