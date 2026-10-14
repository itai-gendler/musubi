---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor enters an email and passphrase that do not match an account
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
- text: The Product refuses the sign-in
  kind: product
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
---

# Refuse a wrong email or passphrase

## Trigger

A person mistypes their details.

## Outcome

They stay on the sign-in page with a message to check their details.
