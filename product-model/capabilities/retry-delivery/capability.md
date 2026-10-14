---
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/task_delivery.ts#handlerRetryTaskDelivery}
- {kind: code, role: implementation, target: apps/api/src/handlers/event_delivery.ts#handlerRetryEventDelivery}
- {kind: code, role: implementation, target: packages/db/src/queries/task-delivery-status.ts#requestTaskDeliveryRetry}
---

# Retry delivery

A user looks at where the changes to an event or task stand at each provider calendar and retries a change the provider did not take, once its cause is fixed. Retry repeats the saved change; it never sends a new one.
