---
entryPoints:
- {web: '/delete-account?token={token}'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/pages.ts#handlerDeleteAccountPage}
---

# Confirm account deletion

The page an account-deletion email links to, where the deletion is confirmed.
