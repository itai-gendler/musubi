---
entities:
- {entity: calendar, shows: [Name]}
- {entity: calendar-membership, shows: [Role], collects: [Role]}
- {entity: user, shows: [Name, Photo]}
references:
- {kind: code, role: implementation, target: apps/client/components/calendar/MemberRolesModal.tsx}
---

# Members

One calendar's members and their roles.
