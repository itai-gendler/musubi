---
appliesTo:
- {type: entity, id: connected-account, effect: creates}
permits:
- related: [{verb: connects, entity: user}]
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts#handlerDisconnectAccount}
- {kind: code, role: implementation, target: apps/api/src/handlers/caldav.ts#handlerConnectCaldav}
---

# Only its user connects a connected account

A connected account belongs to the user who connected it; nobody else, owner of a shared calendar included, reconnects or disconnects it.
