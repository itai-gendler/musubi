---
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/event_notifications.ts#describeChange}
- {kind: code, role: implementation, target: apps/api/src/notification_dispatch.ts#drainPendingNotifications}
---

# Email event changes

When an event someone answered Going or Maybe moves or is cancelled, Musubi emails them about it a few minutes later, unless they turned event change emails off or made the change themselves.
