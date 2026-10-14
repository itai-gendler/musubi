---
appliesTo:
- {type: capability, id: join-calendar}
- {type: capability, id: create-invite-link}
- {type: capability, id: revoke-invite-link}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#getCalendarIDFromToken}
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#joinCalendarFromInvite}
---

# An invite link stops working once it expires, is used up or is revoked

A link is checked every time it is opened or used: past its expiry, at its people limit, or revoked, it opens nothing. A person who is already a member uses up nothing by opening it again.
