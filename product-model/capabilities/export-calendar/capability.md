---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerExportCalendar}
---

# Export calendar

Any member downloads a calendar as an iCalendar (.ics) file with all its events, repeats included.
