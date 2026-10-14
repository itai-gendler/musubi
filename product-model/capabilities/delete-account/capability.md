---
domain: account
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
- {place: 'web::visitor'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/users.ts#handlerDeleteUser}
- {kind: code, role: implementation, target: apps/api/src/handlers/users.ts#handlerConfirmDeleteUser}
- {kind: code, role: implementation, target: packages/db/src/queries/users.ts#deleteUserWithCalendarRevisions}
---

# Delete account

A user deletes their account. Asking only sends a confirmation link to their address; the account goes when the link is confirmed, with every calendar it owns and every event and task it created.
