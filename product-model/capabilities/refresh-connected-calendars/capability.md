---
domain: connections
availability:
- {place: 'web::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts#handlerSyncConnections}
---

# Refresh connected calendars

A user asks Musubi to sync their connected accounts now rather than wait for the next scheduled sync.
