---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerCreateCalendar}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/calendar-dialogs.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/CreateCalendarModal.tsx}
---

# Create calendar

A user creates a calendar with a name and colour and becomes its owner. It can be a Musubi calendar or, for a connected account that allows it, a new calendar created at the provider and synced from then on.
