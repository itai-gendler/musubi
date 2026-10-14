---
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/index.ts#syncExternalAccounts}
- {kind: code, role: implementation, target: apps/api/src/sync/engine.ts#syncUser}
- {kind: doc, role: context, target: packages/docs/src/content/docs/architecture/sync.mdx, title: Sync engine}
---

# Sync connected calendars

Every few minutes — five unless the operator sets otherwise, or never when set to zero — Musubi reads each connected account's calendars and brings their changes in: new, changed, cancelled and removed events, and new calendars. Members with the app open are told to refresh.
