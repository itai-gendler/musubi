---
appliesTo:
- {type: capability, id: link-task}
- {type: capability, id: copy-task}
references:
- {kind: code, role: implementation, target: packages/types/src/calendar.ts#calendarSupportsTaskLinks}
---

# Microsoft To Do lists take independent copies, never live links

A task is linked live only into Musubi calendars, Google Tasks lists and CalDAV task lists; a Microsoft To Do list, or any calendar that cannot keep live links, takes an independent copy instead.
