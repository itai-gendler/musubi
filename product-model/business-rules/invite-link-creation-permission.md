---
appliesTo:
- {type: entity, id: invite-link, effect: creates}
permits:
- related: [{verb: has, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerCreateCalendarInvite}
- {kind: code, role: implementation, target: packages/types/src/permissions.ts#can}
---

# Owners and editors create invite links

Inviting is open to the calendar's owner and editors, by link or by email; viewers cannot invite.
