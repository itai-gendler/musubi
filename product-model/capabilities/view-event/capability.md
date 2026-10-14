---
domain: events
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventDetailsPopover.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/EventDetailModal.tsx}
- {kind: code, role: implementation, target: apps/api/src/permissions.ts#assertCanViewEvent}
---

# View event

Any member of a calendar an event is linked into opens it: when it is, which of the user's calendars it is in with its home marked, location, link, notes, the attendees and their answers, and the user's reminder for it.
