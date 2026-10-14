---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor opens an old reset link and enters a new passphrase
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::reset-passphrase'}
- text: The Product refuses the change
  kind: product
  entities: []
  contexts:
    web: {place: 'web::visitor::reset-passphrase'}
---

# Refuse an expired reset link

## Trigger

A person opens a reset link more than an hour old.

## Outcome

Nothing changes; they ask for a new link.
