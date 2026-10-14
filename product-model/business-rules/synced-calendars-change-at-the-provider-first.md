---
appliesTo:
- {type: capability, id: create-calendar}
- {type: capability, id: edit-calendar}
- {type: capability, id: delete-calendar}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerCreateCalendar}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerUpdateCalendar}
---

# A synced calendar is created, changed or deleted at the provider first

Creating a calendar at a connected account, renaming or recolouring a synced calendar and deleting one happen at the provider first; if the provider refuses, nothing changes in Musubi.
