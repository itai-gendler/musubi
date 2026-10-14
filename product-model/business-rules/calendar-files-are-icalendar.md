---
appliesTo:
- {type: capability, id: import-calendar}
- {type: capability, id: export-calendar}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#assertImportEventLimit}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerExportCalendar}
---

# Calendars move in and out as iCalendar files of up to 10,000 events

Imports and exports are iCalendar (.ics) files with repeats kept. An import holds at most 10,000 events and is refused whole, before anything is created, when it cannot be read.
