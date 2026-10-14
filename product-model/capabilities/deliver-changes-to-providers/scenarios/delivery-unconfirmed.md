---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: A delivery creating an item is waiting
  kind: condition
  unattended: true
  entities: [{entity: delivery, effect: reads, facts: [Destination, Operation]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product sends the creation and no answer comes back
  kind: product
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product records the delivery as unconfirmed
  kind: product
  entities: [{entity: delivery, effect: changes, from: Pending, to: Unconfirmed, facts: [Issue]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
---

# The answer to a creation is lost

## Trigger

A creation was sent but no answer came back.

## Outcome

The delivery shows as unconfirmed and is not sent again blindly, since the item may already exist at the provider.

## Edge cases

- A CalDAV creation has a known address, so Musubi checks it by reading rather than leaving it unconfirmed.
