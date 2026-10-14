---
kind: primary
routes:
  web: Web
steps:
- text: The User types part of a title
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::search'}
- text: The Product lists matching events, a repeating one once as its series, and matching tasks
  kind: product
  actor: user
  entities: [{entity: event, effect: reads, facts: [Title, Starts, Calendars]}, {entity: task, effect: reads, facts: [Title, Due, Status]}]
  contexts:
    web: {place: 'web::signed-in::search'}
---

# Search events and tasks

## Trigger

A user looks for something without knowing when it is.

## Outcome

Matching events and tasks are listed, those in the current view first, and each opens its details.

## Edge cases

- Nothing matching shows No matches.
- Search needs the server; it is not offered from the offline copy.
