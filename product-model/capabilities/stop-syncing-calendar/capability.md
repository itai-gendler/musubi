---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts#handlerDisconnectExternalCalendar}
---

# Stop syncing calendar

The person whose account a synced calendar comes from stops syncing that one calendar. It leaves Musubi with its events, stays untouched at the provider, and is not brought back by later syncs while the account stays connected.
