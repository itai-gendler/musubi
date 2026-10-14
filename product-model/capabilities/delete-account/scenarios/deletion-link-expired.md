---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor opens an old deletion link and confirms
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::confirm-deletion'}
- text: The Product says the link is invalid or has expired
  kind: product
  entities: []
  contexts:
    web: {place: 'web::visitor::confirm-deletion'}
---

# Refuse an expired deletion link

## Trigger

A person opens a deletion link more than an hour old, or one already used.

## Outcome

Nothing is deleted.
