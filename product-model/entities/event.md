---
relations:
- {entity: attendance, verb: has, cardinality: one-to-many}
- {entity: event-reminder, verb: has, cardinality: one-to-many}
- {entity: change-notice, verb: prompts, cardinality: one-to-many}
- {entity: delivery, verb: causes, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: packages/types/src/event.ts#EventSchema}
- {kind: code, role: implementation, target: packages/db/src/schema.ts}
---

# Event

Something happening at a time. One event can be linked into several calendars and is the same event in each; its home calendar decides who may change it.

## Information kept

- **Title** — what it is
- **Starts** — when it starts
- **Ends** — when it ends; an all-day event ends on the day after its last day
- **All day** — whether it takes whole days rather than a time
- **Repeat** — how it repeats, with the dates a series skips or adds, or not at all
- **Location** — where it happens
- **Link** — a web link that goes with it
- **Description** — notes about it
- **Allow attendance** — whether people who can see it answer whether they are coming
- **Color** — the colour of its home calendar
- **Home calendar** — the calendar that owns it: its owners and editors change it and delete it everywhere
- **Calendars** — every calendar it is linked into, the home calendar included

## States

### Scheduled

It is on.

### Cancelled

The provider of a synced calendar reports it called off; it stays visible as cancelled and no longer reminds anyone.
