---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a calendar that cannot keep a live link
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Live task links]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product refuses the link and suggests an independent copy
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Offer a copy where a live link is not possible

## Trigger

The chosen calendar is a Microsoft To Do list or cannot keep live links.

## Outcome

No link is made; the user is told to make an independent copy instead.
