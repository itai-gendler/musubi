---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User saves changes to an event
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The event changed since the user opened it
  kind: condition
  entities: [{entity: event, effect: reads, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product refuses the save and shows the current event
  kind: product
  actor: user
  entities: [{entity: event, effect: reads, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Refuse an edit to an event that changed meanwhile

## Trigger

Someone else saved the event after the user opened it.

## Outcome

Nothing is overwritten; the user sees the current event and their draft is kept to try again.
