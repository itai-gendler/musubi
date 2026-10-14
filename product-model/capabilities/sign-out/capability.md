---
domain: account
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/offline/sign-out.ts}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/settings.tsx}
---

# Sign out

A user signs out of Musubi on this browser or phone.
