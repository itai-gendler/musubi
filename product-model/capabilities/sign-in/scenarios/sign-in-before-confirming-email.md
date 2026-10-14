---
kind: validation
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
- text: The server requires confirmation and the address is not confirmed
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Email confirmed]}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
- text: The Product refuses the sign-in and emails a new confirmation link
  kind: product
  entities: [{entity: user, effect: reads, facts: [Email]}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-in'}
---

# Refuse sign-in before the email is confirmed

## Trigger

A person whose address is unconfirmed signs in on a server that requires confirmation.

## Outcome

The sign-in is refused, a fresh confirmation link is emailed, and the page says to open it rather than blaming the passphrase.

## Edge cases

- Turning the requirement on later also stops existing unconfirmed accounts at their next sign-in, which mails them a link.
