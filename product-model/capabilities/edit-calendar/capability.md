---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerUpdateCalendar}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/calendar-dialogs.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/CalendarSettingsModal.tsx}
---

# Edit calendar

The owner of a calendar renames it or changes its colour. Every member sees the change at once; a synced calendar is changed at the provider first.
