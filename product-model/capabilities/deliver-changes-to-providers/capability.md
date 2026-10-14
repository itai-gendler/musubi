---
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/sync/engine.ts}
- {kind: code, role: implementation, target: apps/api/src/sync/delivery_policy.ts}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/guides/shared-tasks.mdx, title: Saved locally versus delivered remotely}
---

# Deliver changes to providers

Musubi delivers the changes it saved for synced calendars to their providers on its own, in order, and keeps each delivery's state through restarts.
