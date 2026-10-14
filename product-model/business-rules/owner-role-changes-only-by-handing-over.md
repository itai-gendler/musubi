---
appliesTo:
- {type: capability, id: change-member-role}
- {type: capability, id: transfer-ownership}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#transferCalendarOwnership}
---

# The owner's role changes only by handing the calendar over

The owner's own role is never changed directly. Making another member the owner makes the previous owner an editor, in one step, so a calendar always has exactly one owner.
