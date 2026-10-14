---
domain: account
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/AccountPanel.tsx}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/settings.tsx}
---

# Change display name

A user changes the name people they share calendars with see.
