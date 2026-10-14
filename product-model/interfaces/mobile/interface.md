---
type: mobile-app
actors:
- visitor
- user
entryPoints:
- {mobile-app: 'musubi://invite/{token}'}
- {web: '/invite/{token}'}
references:
- {kind: code, role: implementation, target: apps/client/app/_layout.tsx}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/_layout.tsx}
- {kind: code, role: implementation, target: 'apps/client/app/invite/[token].tsx'}
---

# Musubi phone app

The Android and iOS app: Home with the month, week, day and agenda views, Tasks,
Calendars and Settings, with local reminders. It works against the hosted server
or a self-hosted one.
