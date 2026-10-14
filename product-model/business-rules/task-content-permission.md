---
appliesTo:
- {type: entity, id: task, effect: changes, facts: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Completed at]}
permits:
- related: [{verb: homes, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerUpdateTask}
- {kind: code, role: implementation, target: packages/db/src/queries/tasks.ts#taskReadableMembership}
---

# Only owners and editors of its home calendar change or complete a task

A task's content, status and priority change through its home calendar alone. To let someone complete a shared task, make them an editor of its home; editing rights on another calendar it is linked into only manage that link.
