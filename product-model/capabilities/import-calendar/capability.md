---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerImportCalendar}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#assertImportEventLimit}
---

# Import calendar

A user imports an iCalendar (.ics) file as a new calendar they own, as a Musubi calendar or into a connected account.
