---
entities:
- {entity: delivery, shows: [Destination, Operation, Issue]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/TaskDeliveryDialog.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/EventDeliveryDialog.tsx}
---

# Delivery

Where the changes to one event or task stand at each provider calendar they go to, with retrying the ones that can be retried.
