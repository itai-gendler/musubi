---
appliesTo:
- {type: entity, id: invite-link, effect: removes}
permits:
- related: [{verb: has, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerRevokeInvite}
---

# Owners and editors revoke invite links

Whoever may create a calendar's invite links may also revoke them.
