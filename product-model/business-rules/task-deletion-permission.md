---
appliesTo:
- {type: entity, id: task, effect: removes}
permits:
- related: [{verb: homes, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerRemoveTask}
---

# Only owners and editors of its home calendar delete a task

Deleting a task deletes it everywhere, so it needs editing rights on its home.
