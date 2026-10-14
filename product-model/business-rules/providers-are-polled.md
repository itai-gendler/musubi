---
appliesTo:
- {type: capability, id: sync-connected-calendars}
- {type: capability, id: refresh-connected-calendars}
references:
- {kind: code, role: implementation, target: apps/api/src/index.ts#syncExternalAccounts}
- {kind: code, role: implementation, target: packages/config/src/index.ts}
---

# Provider calendars are read on a schedule

Musubi reads connected accounts every five minutes unless the operator sets another interval, or none; a user can also refresh on demand. Providers never push changes to Musubi.
