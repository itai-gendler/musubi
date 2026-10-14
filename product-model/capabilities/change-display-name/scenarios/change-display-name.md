---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters a new display name
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product saves the name
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
---

# Change the display name

## Trigger

A user wants to be recognized differently.

## Outcome

Their new name shows in members lists, attendee lists and invitations.
