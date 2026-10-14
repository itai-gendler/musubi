---
appliesTo:
- {type: entity, id: task, effect: creates}
permits:
- related: [{verb: homes, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerCreateTask}
- {kind: code, role: implementation, target: packages/types/src/permissions.ts#can}
---

# Owners and editors of its home create a task

A task is created by an owner or editor of the calendar that becomes its home, which must keep tasks.
