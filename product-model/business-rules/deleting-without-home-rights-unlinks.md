---
appliesTo:
- {type: capability, id: delete-event}
- {type: capability, id: unlink-event}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerRemoveEvent}
---

# Deleting an event without rights on its home only unlinks it

When someone who edits some of an event's calendars, but not its home, deletes it, the event leaves the calendars they edit and stays in the rest.
