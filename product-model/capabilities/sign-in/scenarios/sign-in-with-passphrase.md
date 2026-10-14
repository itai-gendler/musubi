---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor enters their email and passphrase
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
- text: The Product checks them against the account and signs the person in
  kind: product
  actor: visitor
  entities: [{entity: user, effect: reads, facts: [Email, Passphrase, Email confirmed]}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
---

# Sign in with email and passphrase

## Trigger

A person with an account comes back to Musubi.

## Outcome

They are signed in and see their calendar, or the invitation they were opening.

## Edge cases

- On the phone, the welcome screen is reached first, where the server to use is chosen (Choose server).
