---
domain: sharing
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerRevokeInvite}
---

# Revoke invite link

An owner or editor revokes an invite link; it stops working at once, however it was passed on.
