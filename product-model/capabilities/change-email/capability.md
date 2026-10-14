---
domain: account
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
- {place: 'web::visitor'}
references:
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/AccountPanel.tsx}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/settings.tsx}
---

# Change email

A user moves their account to another email address. A confirmed account is asked to approve the move at its current address; an unconfirmed one confirms the new address instead.
