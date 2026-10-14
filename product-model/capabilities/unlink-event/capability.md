---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/client/components/calendar/EventDetailModal.tsx}
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerRemoveEvent}
---

# Unlink event

A user takes an event out of one calendar that is not its home and that they edit. It stays in its home and other calendars.
