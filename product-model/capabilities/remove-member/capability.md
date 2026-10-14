---
domain: sharing
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerKickMember}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#removeCalendarMember}
---

# Remove member

The owner removes a member from a calendar; the calendar disappears from that person's devices.
