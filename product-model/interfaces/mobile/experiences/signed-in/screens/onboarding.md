---
entities:
- {entity: user, collects: [Name, Photo]}
- {entity: calendar, collects: [Name, Color]}
references:
- {kind: code, role: implementation, target: apps/client/app/onboarding/index.tsx}
- {kind: code, role: implementation, target: apps/client/app/onboarding/calendar.tsx}
- {kind: code, role: implementation, target: apps/client/app/onboarding/sync.tsx}
- {kind: code, role: implementation, target: apps/client/app/onboarding/share.tsx}
---

# Welcome

The first-run set-up: name and photo, the personal calendar, connecting calendars and a calendar to share.
