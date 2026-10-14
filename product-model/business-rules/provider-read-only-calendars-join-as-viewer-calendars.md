---
appliesTo:
- {type: capability, id: connect-calendar-account}
- {type: capability, id: sync-connected-calendars}
references:
- {kind: code, role: implementation, target: apps/api/src/sync/engine.ts}
---

# A calendar read-only at its provider is a viewer's calendar in Musubi

A synced calendar the provider lets the account only read is brought in with its person as a viewer, so it cannot be renamed, deleted or shared for editing in Musubi, and its events change only as far as the provider allows; one the account may write is brought in with them as owner.
