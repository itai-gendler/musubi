---
domain: calendars
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/reminders.ts#handlerPutCalendarReminder}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/calendar-dialogs.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/CalendarSettingsModal.tsx}
---

# Change calendar reminder

Any member, viewers included, sets when the events of one calendar remind them, or returns to their default. The rule is theirs alone: other members' reminders do not change.
