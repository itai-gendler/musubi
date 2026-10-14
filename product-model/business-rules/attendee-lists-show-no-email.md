---
appliesTo:
- {type: capability, id: view-event}
- {type: capability, id: answer-event}
- {type: capability, id: change-member-role}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerGetCalendarMembers}
- {kind: doc, role: context, target: packages/docs/src/content/docs/architecture/data-model.mdx, title: Data model}
---

# Attendee and member lists never show email addresses

People who share a calendar or an event see each other's names and photos, not their email addresses: an event can span calendars whose members do not know each other.
