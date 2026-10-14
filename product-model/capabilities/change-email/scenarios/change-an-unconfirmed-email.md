---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters the new email address
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The current address is not confirmed
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Email confirmed]}]
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product emails a confirmation link to the new address
  kind: product
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Visitor opens the link at the new address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor'}
    mobile: {place: 'web::visitor'}
- text: The Product moves the account to the new, confirmed address
  kind: product
  actor: visitor
  entities: [{entity: user, effect: changes, facts: [Email, Email confirmed]}]
  contexts:
    web: {place: 'web::visitor'}
    mobile: {place: 'web::visitor'}
---

# Change an unconfirmed email address

## Trigger

A user whose address was never confirmed changes it.

## Outcome

The new address is confirmed by its own link.
