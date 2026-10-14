---
appliesTo:
- {type: capability, id: delete-calendar}
- {type: capability, id: stop-syncing-calendar}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#removeCalendarInTransaction}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/architecture/data-model.mdx, title: Data model}
---

# Deleting a calendar deletes the events and tasks whose home it is

The events and tasks homed in a deleted calendar are deleted from every calendar they were linked into. Those only linked into it stay in their other calendars with their home unchanged.
