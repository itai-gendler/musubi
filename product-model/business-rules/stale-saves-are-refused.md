---
appliesTo:
- {type: capability, id: edit-event}
- {type: capability, id: delete-event}
- {type: capability, id: edit-task}
- {type: capability, id: edit-page}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerUpdateEvent}
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerUpdateTask}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendar_pages.ts#handlerSavePage}
---

# A save based on an older version is refused

Events, tasks and pages carry a version; a change made against a version someone else has since replaced is refused instead of overwriting theirs, and the person's draft is kept.
