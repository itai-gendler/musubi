---
domain: sharing
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerSetMemberRole}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#setCalendarMemberRole}
---

# Change member role

The owner makes a member an editor or a viewer. The member's devices pick up the change at once.
