---
appliesTo:
- {type: entity, id: invite-link, effect: reads, contexts: [{place: 'web::signed-in::sharing'}, {place: 'mobile::signed-in::invite-links'}]}
permits:
- related: [{verb: has, entity: calendar}, {verb: has, entity: calendar-membership}, {verb: holds, entity: user}]
  when:
  - {entity: calendar-membership, fact: Role, is-not: Viewer}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerGetCalendarInvites}
---

# Only owners and editors see a calendar's invite links

The list of a calendar's invite links is shown to its owner and editors only; viewers do not see them.
