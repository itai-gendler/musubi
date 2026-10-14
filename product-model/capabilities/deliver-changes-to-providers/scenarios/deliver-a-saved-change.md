---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: A delivery is waiting and the ones before it went through
  kind: condition
  unattended: true
  entities: [{entity: delivery, effect: reads, facts: [Destination, Operation]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product sends the change to the provider through the connected account
  kind: product
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product marks the delivery delivered
  kind: product
  entities: [{entity: delivery, effect: changes, from: Pending, to: Delivered, facts: []}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
---

# Deliver a saved change

## Trigger

A change to a synced calendar is waiting.

## Outcome

The provider has the change and the delivery shows as delivered.
