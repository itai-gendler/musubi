---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens the delivery details from the item's actions or the list of pending deliveries
  kind: actor
  actor: user
  entities: [{entity: delivery, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product shows each destination with its operation, state and issue
  kind: product
  actor: user
  entities: [{entity: delivery, effect: reads, facts: [Destination, Operation, Issue]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The User chooses Retry on a change that was not written
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The user still edits the destination calendar and the change before it went through
  kind: condition
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product queues the saved change again
  kind: product
  actor: user
  entities: [{entity: delivery, effect: changes, from: Not written, to: Pending, facts: []}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
---

# Retry a delivery

## Trigger

A change to a synced calendar was not written, for example because the account needed reconnecting.

## Outcome

The change is queued again and goes out with the next delivery.

## Edge cases

- On the web, unresolved deliveries also show in the notification centre; on the phone, Settings lists them all.
