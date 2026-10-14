---
appliesTo:
- {type: entity, id: invite-link, effect: changes, facts: [Uses]}
permits:
- actors:
  - user
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#joinCalendarFromInvite}
---

# Anyone holding a live invite link uses it to join

Joining counts a use of the link; whoever has the link and an account may use it while it is live.
