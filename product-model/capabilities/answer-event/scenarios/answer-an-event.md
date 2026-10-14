---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks Going, Maybe or Declined
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The event allows attendance
  kind: condition
  entities: [{entity: event, effect: reads, facts: [Allow attendance]}, {entity: attendance, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product records the answer and updates the attendee list for everyone who can see the event
  kind: product
  actor: user
  entities: [{entity: attendance, effect: creates, facts: [Answer]}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Answer an event

## Trigger

A user says whether they are coming.

## Outcome

Their answer shows to everyone who can see the event.

## Edge cases

- A viewer answers as much as an owner does: answering is not editing.
- Turning attendance off keeps the answers; turning it on again brings them back.
