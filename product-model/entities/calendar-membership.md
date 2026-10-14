---
references:
- {kind: code, role: implementation, target: packages/types/src/permissions.ts#can}
- {kind: code, role: implementation, target: packages/db/src/schema.ts}
---

# Membership

A user's place in one calendar, and the role they hold there. Every calendar has exactly one member who is its owner.

## Information kept

- **Role** — Owner, who also renames, deletes and hands over the calendar and manages its members; Editor, who adds and changes events and tasks homed there and shares invite links; or Viewer, who sees it
- **Reminder** — this member's own reminder rule for the calendar's events, including never, or none to follow their default
