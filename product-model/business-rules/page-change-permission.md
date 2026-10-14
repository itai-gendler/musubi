---
appliesTo:
- {type: entity, id: page, effect: changes}
permits:
- related: [{verb: keeps, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendar_pages.ts}
- {kind: code, role: implementation, target: packages/db/src/queries/pages.ts}
---

# Only its user changes a page

Pages are private to the user who keeps them; they are never shared, even with members of the same calendars.
