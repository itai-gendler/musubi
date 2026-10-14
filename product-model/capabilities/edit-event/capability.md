---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerUpdateEvent}
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerEventScope}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/RecurrenceScopeDialog.tsx}
- {kind: code, role: implementation, target: apps/api/src/event_notifications.ts#queueEventChange}
---

# Edit event

An owner or editor of an event's home calendar changes it, in the editor or by dragging it on the grid, and the change shows in every calendar it is linked into. A repeating event is changed for one occurrence, this and following ones, or all.
