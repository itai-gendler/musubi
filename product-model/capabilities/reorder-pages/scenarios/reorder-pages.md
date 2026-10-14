---
kind: primary
routes:
  web: Web
steps:
- text: The User drags a page to a new place in the list
  kind: actor
  actor: user
  entities: [{entity: page, effect: reads, facts: [Name, Position]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
- text: The Product saves the new order
  kind: product
  actor: user
  entities: [{entity: page, effect: changes, facts: [Position]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
---

# Reorder pages

## Trigger

A user wants their pages in another order.

## Outcome

The pages are listed in the new order.
