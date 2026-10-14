---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: A delivery is waiting
  kind: condition
  unattended: true
  entities: [{entity: delivery, effect: reads, facts: [Destination, Operation]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product sends the change and the provider refuses it, or refuses the account's access
  kind: product
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product records the delivery as not written, with the issue
  kind: product
  entities: [{entity: delivery, effect: changes, from: Pending, to: Not written, facts: [Issue]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
---

# Provider does not take the change

## Trigger

The provider refuses the change, or the account needs reconnecting.

## Outcome

The delivery shows it was not written and why; the change saved in Musubi stays.
