---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User drags the event to a new time or changes its length
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product saves the new time
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Starts, Ends]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product queues a notice of the move for each attendee who did not decline, except the user
  kind: product
  actor: user
  entities: [{entity: attendance, effect: reads, facts: [Answer]}, {entity: change-notice, effect: creates, to: Queued, facts: [Change, Was, Now]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# Move an event by dragging it

## Trigger

A user drags an event to another time, or stretches it.

## Outcome

The event takes the new time; attendees who did not decline are told by email a few minutes later.
