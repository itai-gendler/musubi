---
domain: sharing
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerLeaveCalendar}
---

# Leave calendar

A member who is not the owner leaves a calendar. It and its events stay for everyone else.
