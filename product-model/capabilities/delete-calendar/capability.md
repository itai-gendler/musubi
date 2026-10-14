---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerRemoveCalendar}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#removeCalendarInTransaction}
---

# Delete calendar

The owner deletes a calendar. The events and tasks whose home it is are deleted everywhere they are linked; events and tasks only linked into it stay in their other calendars.
