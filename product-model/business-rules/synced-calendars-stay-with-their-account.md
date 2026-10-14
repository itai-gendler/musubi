---
appliesTo:
- {type: capability, id: transfer-ownership}
- {type: capability, id: edit-calendar}
- {type: capability, id: delete-calendar}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#transferCalendarOwnership}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerUpdateCalendar}
---

# A synced calendar's ownership is never transferred

A calendar synced from a provider stays with the person whose connected account it comes from; only they change or delete it, and nobody can be made its owner.

## Rationale

The provider only accepts changes from the account that holds the credentials, so an owner without them could change nothing there.
