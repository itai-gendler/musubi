---
entities:
- {entity: calendar, shows: [Name]}
- {entity: calendar-membership, shows: [Role], collects: [Role]}
- {entity: user, shows: [Name, Photo]}
- {entity: invite-link, shows: [Expires, People limit, Uses], collects: [Expires, People limit]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/ShareCalendarDialog.tsx}
---

# Sharing

One calendar's members and their roles, its active invite links and inviting people by email.
