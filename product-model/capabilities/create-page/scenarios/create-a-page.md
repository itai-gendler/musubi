---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses New page and enters a name, icon and view
  kind: actor
  actor: user
  entities: [{entity: page, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::new-page'}
- text: The Product creates the page at the end of the list and opens it
  kind: product
  actor: user
  entities: [{entity: page, effect: creates, facts: [Name, Icon, View, Item types, Calendars shown, Default, Position]}]
  contexts:
    web: {place: 'web::signed-in::new-page'}
---

# Create a page

## Trigger

A user wants a separate view for work, family or a plan.

## Outcome

The new page is in the list of pages and opens.
