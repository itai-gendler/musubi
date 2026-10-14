---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/events.ts#handlerSetAttendance}
---

# Answer event

On an event that allows attendance, anyone who can see it answers Going, Maybe or Declined, changes the answer, or clears it. Everyone who can see the event sees the answers live.
