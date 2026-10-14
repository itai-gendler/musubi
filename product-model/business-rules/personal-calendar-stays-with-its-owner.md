---
appliesTo:
- {type: capability, id: delete-calendar}
- {type: capability, id: transfer-ownership}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerRemoveCalendar}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#transferCalendarOwnership}
---

# A personal calendar is never deleted or handed over

Every account gets a personal calendar when it is created. It cannot be deleted, and its ownership cannot be transferred.
