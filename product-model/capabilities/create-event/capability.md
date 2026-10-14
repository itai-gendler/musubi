---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerCreateEvent}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventEditorForm.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/AddEventModal.tsx}
- {kind: code, role: implementation, target: apps/client/lib/eventForm.ts}
---

# Create event

An owner or editor of a calendar creates an event in it, or in several calendars at once with one of them as its home. On a synced calendar the event is saved in Musubi first and delivered to the provider after.
