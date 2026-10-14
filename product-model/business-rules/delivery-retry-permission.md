---
appliesTo:
- {type: entity, id: delivery, effect: changes}
permits:
- related: [{verb: carries, entity: connected-account}, {verb: connects, entity: user}]
- unattended: true
references:
- {kind: code, role: implementation, target: packages/db/src/queries/task-delivery-status.ts#requestTaskDeliveryRetry}
---

# Only the person whose account carries a delivery retries it

A delivery is retried by the person whose connected account carries it, while they are still an owner or editor of the destination calendar. Musubi itself moves deliveries along as it sends them.
