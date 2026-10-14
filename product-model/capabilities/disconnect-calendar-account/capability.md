---
domain: connections
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts#handlerDisconnectAccount}
---

# Disconnect calendar account

A user disconnects one connected account. Its synced calendars leave Musubi; nothing is deleted at the provider, and Google's grant is revoked.
