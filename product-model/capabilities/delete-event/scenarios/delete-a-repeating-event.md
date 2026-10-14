---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Delete on an occurrence
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: [Repeat]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The User chooses this event, this and following events, or the entire series
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product skips that date, ends the series before it, or deletes the series
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Repeat]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Delete part of a repeating event

## Trigger

A user deletes an occurrence of a repeating event.

## Outcome

Only the chosen occurrences are gone.

## Edge cases

- Deleting the entire series removes the event as in a plain delete.
