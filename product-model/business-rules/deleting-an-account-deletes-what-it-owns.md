---
appliesTo:
- {type: capability, id: delete-account}
- {type: capability, id: delete-calendar}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/users.ts#deleteUserWithCalendarRevisions}
---

# Deleting an account deletes its calendars and everything it created

When an account is deleted, the calendars it owns go for every member they were shared with, and the events and tasks it created go wherever they were linked, including calendars other people own. Deletion is not a transfer of ownership.
