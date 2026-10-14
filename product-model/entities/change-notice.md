---
references:
- {kind: code, role: implementation, target: apps/api/src/event_notifications.ts#queueEventChange}
- {kind: code, role: implementation, target: apps/api/src/notification_dispatch.ts#drainPendingNotifications}
---

# Change notice

An email Musubi owes an attendee because an event they are coming to moved or was cancelled. Notices wait a few minutes so that quick successive changes go out together.

## Information kept

- **Change** — moved or cancelled
- **Was** — when it used to start
- **Now** — when it starts now

## States

### Queued

Waiting to be sent.

### Sent

Emailed to the attendee.
