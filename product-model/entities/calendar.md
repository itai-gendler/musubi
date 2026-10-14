---
relations:
- {entity: calendar-membership, verb: has, cardinality: one-to-many}
- {entity: invite-link, verb: has, cardinality: one-to-many}
- {entity: event, verb: homes, cardinality: one-to-many}
- {entity: event, verb: lists, cardinality: many-to-many}
- {entity: task, verb: homes, cardinality: one-to-many}
- {entity: task, verb: lists, cardinality: many-to-many}
- {entity: delivery, verb: receives, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: packages/types/src/calendar.ts#CalendarSchema}
- {kind: code, role: implementation, target: packages/db/src/schema.ts}
---

# Calendar

A named, coloured place where events and tasks appear, kept by Musubi itself or synced from a connected Google, Outlook, iCloud or other CalDAV account. It is shared by giving people a membership in it.

## Information kept

- **Name** — what it is called, up to 80 characters
- **Color** — its colour, from Musubi's palette or the provider's
- **Personal** — whether it is the personal calendar Musubi made for its owner's account
- **Provider** — none for a Musubi calendar, or Google Calendar, Outlook, iCloud or another CalDAV server for a synced one
- **Supports tasks** — whether tasks can be kept in it
- **Live task links** — whether it can keep live links to tasks homed elsewhere: Musubi, Google Tasks and CalDAV task lists can, Microsoft To Do lists cannot
