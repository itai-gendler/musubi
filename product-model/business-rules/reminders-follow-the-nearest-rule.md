---
appliesTo:
- {type: capability, id: remind-of-events}
- {type: capability, id: change-event-reminder}
- {type: capability, id: change-calendar-reminder}
- {type: capability, id: reorder-calendars}
references:
- {kind: code, role: implementation, target: packages/calendar/src/reminders.ts#resolveReminders}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/reference/reminders.mdx, title: Reminders}
---

# An event reminds by the nearest rule that has an answer

For each person, an event follows their own reminder for it; else the rule of the first of its calendars, in their calendar order, that has one; else their default. Never is an answer like any other.
