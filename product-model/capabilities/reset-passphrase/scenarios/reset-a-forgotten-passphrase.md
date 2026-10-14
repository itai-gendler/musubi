---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor types their email and asks for a new passphrase
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
- text: The Product emails a reset link valid for one hour if the address has an account, and says a link is on its way either way
  kind: product
  entities: [{entity: user, effect: reads, facts: [Email, Name]}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
- text: The Visitor opens the link and enters a new passphrase
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::reset-passphrase'}
    mobile: {place: 'web::visitor::reset-passphrase'}
- text: The Product replaces the passphrase
  kind: product
  actor: visitor
  entities: [{entity: user, effect: changes, facts: [Passphrase]}]
  contexts:
    web: {place: 'web::visitor::reset-passphrase'}
    mobile: {place: 'web::visitor::reset-passphrase'}
---

# Reset a forgotten passphrase

## Trigger

A person cannot remember their passphrase.

## Outcome

The passphrase is the new one and they can sign in with it.

## Edge cases

- A server without mail hides the phone's Forgotten password? control.
- The web asks for the email to be typed first before sending anything.
