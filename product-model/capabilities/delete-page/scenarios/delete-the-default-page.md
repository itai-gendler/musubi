---
kind: alternative
routes:
  web: Web
steps:
- text: The User deletes the default one of their pages
  kind: actor
  actor: user
  entities: [{entity: page, as: deleted, effect: reads, facts: [Default]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The Product deletes it and makes the first remaining page the default
  kind: product
  actor: user
  entities: [{entity: page, as: deleted, effect: removes}, {entity: page, as: heir, effect: changes, facts: [Default]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
---

# Delete the default page

## Trigger

A user deletes the page Musubi opens on.

## Outcome

The first remaining page in the list becomes the default.
