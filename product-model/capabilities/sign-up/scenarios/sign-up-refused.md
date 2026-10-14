---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor enters a malformed email, a passphrase under 8 characters, or two passphrases that differ
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The Product refuses and keeps the form as typed
  kind: product
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
---

# Refuse an unusable sign-up

## Trigger

A visitor's details cannot make an account.

## Outcome

No account is created and the form says why.

## Edge cases

- An email that already has an account is refused by the server.
