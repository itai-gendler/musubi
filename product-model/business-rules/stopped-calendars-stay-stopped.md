---
appliesTo:
- {type: capability, id: stop-syncing-calendar}
- {type: capability, id: sync-connected-calendars}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts#handlerDisconnectExternalCalendar}
---

# A calendar whose sync was stopped is not brought back

Stopping the sync of one calendar is remembered, so later syncs of its account do not bring it in again while the account stays connected.
