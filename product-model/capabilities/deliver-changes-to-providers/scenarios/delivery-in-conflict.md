---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: A delivery updating an item is waiting
  kind: condition
  unattended: true
  entities: [{entity: delivery, effect: reads, facts: [Destination, Operation]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product finds the item at the provider changed since it was last read
  kind: product
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product records the delivery as in conflict
  kind: product
  entities: [{entity: delivery, effect: changes, from: Pending, to: Conflict, facts: [Issue]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
---

# The item changed at the provider meanwhile

## Trigger

The item changed at the provider in a way the saved change cannot be laid over.

## Outcome

The delivery shows a conflict to be looked at; nothing is overwritten at the provider.
