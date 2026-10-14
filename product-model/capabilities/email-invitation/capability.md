---
domain: sharing
availability:
- {place: 'web::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerSendCalendarInvite}
---

# Email invitation

An owner or editor emails a calendar's invite link to one address, creating a link first when the calendar has none.
