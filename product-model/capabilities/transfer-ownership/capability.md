---
domain: sharing
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerSetMemberRole}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#transferCalendarOwnership}
---

# Transfer ownership

The owner hands a calendar to another member, who takes over its members, invite links and settings; the previous owner becomes an editor.
