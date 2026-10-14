---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses to save their changes as a new page
  kind: actor
  actor: user
  entities: [{entity: page, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The Product creates a copy of the page with the user's changes and opens it
  kind: product
  actor: user
  entities: [{entity: page, effect: creates, facts: [Name, Icon, View, Row height, Weeks shown, Weekend, Nearby months, Item types, Calendars shown, Default, Position]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
---

# Save a page's changes as a new page

## Trigger

A page changed on another device while the user was editing it here.

## Outcome

The user's version is kept as a new page beside the changed one.
