---
kind: edge
routes:
  web: Web
steps:
- text: The User saves the page
  kind: actor
  actor: user
  entities: [{entity: page, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The page changed on another device since it was opened
  kind: condition
  entities: [{entity: page, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The Product says the page changed on another device and keeps the draft
  kind: product
  entities: [{entity: page, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
---

# Refuse to overwrite a page changed elsewhere

## Trigger

The page was saved on another device after the user opened it.

## Outcome

Nothing is overwritten; the user keeps their draft, and can save it as a new page.
