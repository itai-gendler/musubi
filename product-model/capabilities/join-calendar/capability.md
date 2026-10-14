---
domain: connections
availability:
- {place: 'web::visitor'}
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerJoinCalendar}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerGetCalendarFromToken}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#joinCalendarFromInvite}
- {kind: code, role: implementation, target: apps/web/src/routes/invite.$token.tsx}
- {kind: code, role: implementation, target: 'apps/client/app/invite/[token].tsx'}
---

# Join calendar

Someone with an invite link sees the calendar it opens — its name, who shared it, who is on it and the next 30 days — and joins it as a viewer once signed in.
