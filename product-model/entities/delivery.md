---
references:
- {kind: code, role: implementation, target: packages/types/src/task.ts#TaskDeliveryTargetSchema}
- {kind: code, role: implementation, target: packages/types/src/event_delivery.ts}
---

# Delivery

One change Musubi saved and still has to make at a provider: creating, changing or deleting one event or task in one synced calendar. Saving in Musubi and delivering to the provider are separate, so a saved change can still be on its way.

## Information kept

- **Destination** — the synced calendar the change goes to
- **Operation** — create, update or delete
- **Issue** — why it has not gone through: reconnect needed, write refused or unsupported, conflict, unconfirmed or destination unavailable

## States

### Pending

Waiting to be sent, or being sent.

### Delivered

The provider accepted it, or it turned out not to be needed.

### Not written

The provider did not take it; it can be retried once the cause is fixed.

### Unconfirmed

A creation whose answer was lost: it may have happened, so it is never repeated blindly.

### Conflict

The item changed at the provider in a way the change cannot be laid over.
