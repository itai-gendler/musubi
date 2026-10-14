---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerForkEvent}
---

# Copy event

A user makes an independent copy of an event they can see in another calendar they edit. The copy is a new event with the user as organizer and that calendar as its home, and changes separately from then on.
