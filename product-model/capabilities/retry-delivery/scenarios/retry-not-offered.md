---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens the delivery details
  kind: actor
  actor: user
  entities: [{entity: delivery, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The change is unconfirmed, in conflict or unsupported
  kind: condition
  entities: [{entity: delivery, effect: reads, facts: [Issue]}]
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
- text: The Product offers no Retry and says what to check
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::delivery'}
    mobile: {place: 'mobile::signed-in::delivery'}
---

# Refuse to retry what cannot be retried safely

## Trigger

A change is unconfirmed, in conflict, or not supported by the provider.

## Outcome

No retry happens; the user checks the provider or refreshes instead.

## Edge cases

- An unconfirmed creation may already exist at the provider, so it is never repeated.
