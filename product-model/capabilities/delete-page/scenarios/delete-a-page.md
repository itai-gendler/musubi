---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete page and confirms
  kind: actor
  actor: user
  entities: [{entity: page, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The user has another page
  kind: condition
  entities: [{entity: user, effect: reads, facts: []}, {entity: page, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The Product deletes the page
  kind: product
  actor: user
  entities: [{entity: page, effect: removes}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
---

# Delete a page

## Trigger

A user no longer needs a page.

## Outcome

The page is gone from the list; the calendars it showed are untouched.

## Edge cases

- With a single page left, Delete page is not offered.
