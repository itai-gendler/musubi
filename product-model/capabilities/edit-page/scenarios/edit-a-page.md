---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the page's settings and saves
  kind: actor
  actor: user
  entities: [{entity: page, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The Product saves the page
  kind: product
  actor: user
  entities: [{entity: page, effect: changes, facts: [Name, Icon, View, Row height, Weeks shown, Weekend, Nearby months, Item types, Calendars shown]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
---

# Edit a page

## Trigger

A user wants a page to show something different.

## Outcome

The page shows what the user chose.

## Edge cases

- A page set to show all calendars picks up new calendars on its own; one showing chosen calendars does not.
