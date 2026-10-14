---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens the confirmation link from the email
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor'}
- text: The Product confirms the address and signs the person in
  kind: product
  actor: visitor
  entities: [{entity: user, effect: changes, facts: [Email confirmed]}]
  contexts:
    web: {place: 'web::visitor'}
---

# Confirm the address from the emailed link

## Trigger

A person opens the confirmation link within its hour.

## Outcome

The address is confirmed and the person is signed in without typing anything again.

## Edge cases

- A link older than an hour no longer works; signing in again sends a new one.
