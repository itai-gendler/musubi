---
kind: primary
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
- text: The current address is confirmed
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Email confirmed]}]
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product emails an approval link, valid for an hour, to the current address
  kind: product
  actor: user
  entities: [{entity: user, effect: reads, facts: [Email, Name]}]
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Visitor opens the approval link from the current address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor'}
    mobile: {place: 'web::visitor'}
- text: The Product moves the account to the new address
  kind: product
  actor: visitor
  entities: [{entity: user, effect: changes, facts: [Email]}]
  contexts:
    web: {place: 'web::visitor'}
    mobile: {place: 'web::visitor'}
---

# Change a confirmed email address

## Trigger

A user's address changes.

## Outcome

After approval from the current address, the account signs in and receives mail at the new one.
