---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User changes an occurrence and saves
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: [Repeat]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The User chooses this event, this and following events, or all events
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product changes that occurrence alone, splits the series at it, or changes the whole series
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Edit a repeating event

## Trigger

A user changes one occurrence of a repeating event.

## Outcome

Only the chosen occurrences change; the rest of the series stays as it was.

## Edge cases

- An Outlook series offers this occurrence or the entire series.
