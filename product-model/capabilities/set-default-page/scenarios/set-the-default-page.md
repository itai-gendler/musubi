---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Set as default
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::page-settings'}
- text: The Product makes it the default and the previous default an ordinary page
  kind: product
  actor: user
  entities: [{entity: page, as: new-default, effect: changes, facts: [Default]}, {entity: page, as: previous-default, effect: changes, facts: [Default]}]
  contexts:
    web: {place: 'web::signed-in::page-settings'}
---

# Set the default page

## Trigger

A user wants Musubi to open on another page.

## Outcome

That page is the default and the previous default no longer is.
