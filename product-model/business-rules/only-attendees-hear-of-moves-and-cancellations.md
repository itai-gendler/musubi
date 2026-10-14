---
appliesTo:
- {type: capability, id: email-event-changes}
- {type: capability, id: edit-event}
references:
- {kind: code, role: implementation, target: apps/api/src/event_notifications.ts#describeChange}
- {kind: code, role: implementation, target: apps/api/src/event_notifications.ts#queueEventChange}
---

# Only attendees hear that an event moved or was cancelled

A change email goes to people who answered Going or Maybe, never to every member of its calendars, and not to the person who made the change. Only a new time or a cancellation counts as news.

## Rationale

Mailing every member of a shared calendar for each small edit would teach people to ignore Musubi's mail.
