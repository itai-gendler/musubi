---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerRemoveEvent}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventDetailsPopover.tsx}
---

# Delete event

A user deletes an event. With rights on its home calendar it is deleted everywhere; with rights only on some of the calendars it is linked into, it is taken out of those and stays elsewhere. A repeating event is deleted for one occurrence, this and following ones, or the series.
