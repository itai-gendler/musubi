---
relations:
- {entity: delivery, verb: causes, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: packages/types/src/task.ts#TaskSchema}
---

# Task

Something to do, with a status, optional dates and a priority. Like an event it has one home calendar and may be linked live into others, where it is the same task with the same completion.

## Information kept

- **Title** — what is to be done
- **Notes** — a description
- **Status** — Needs action, In progress, Completed or Cancelled
- **Starts** — when work on it starts
- **Due** — when it is due; Google Tasks keeps only the day
- **All day** — whether its dates are days without a time
- **Priority** — none, high, medium or low
- **Repeat** — how it repeats, or not at all
- **Link** — a web link that goes with it
- **Related task** — another task it belongs under
- **Completed at** — when it was completed
- **Home calendar** — the calendar that owns it: its owners and editors change, complete and delete it
- **Calendars** — every calendar it is linked into, the home calendar included
