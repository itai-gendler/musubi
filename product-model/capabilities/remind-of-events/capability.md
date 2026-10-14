---
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: packages/calendar/src/reminders.ts#resolveReminders}
- {kind: code, role: implementation, target: apps/web/src/calendar/use-reminders.ts}
- {kind: code, role: implementation, target: apps/client/services/notifications.ts}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/reference/reminders.mdx, title: Reminders}
---

# Remind of events

Musubi reminds each person of their events at the time their rule says: the event's own choice if they made one, else the rule of the first of its calendars in their order that has one, else their default. The phone schedules reminders itself; the web reminds while a tab is open.
