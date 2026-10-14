---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/app/p.$pageId.$view.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/view-registry.ts}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/index.tsx}
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerGetEvents}
---

# Browse calendar

A user looks through their calendar by day, week, several weeks, month or agenda, with the events and dated tasks of the calendars they show. An event linked into several of their calendars appears once.
