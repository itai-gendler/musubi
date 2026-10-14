---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerLinkEvent}
- {kind: code, role: implementation, target: apps/api/src/event_permissions.ts#hasEventCalendarAccess}
---

# Link event

A user links an event they can see into another calendar they edit. It stays one event: future changes appear in every linked calendar, and its home does not move.
