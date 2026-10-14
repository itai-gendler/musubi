---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Use inherited setting
  kind: actor
  actor: user
  entities: [{entity: event-reminder, effect: reads, facts: [Reminder]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product removes the user's reminder for the event
  kind: product
  actor: user
  entities: [{entity: event-reminder, effect: removes}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Go back to the inherited reminder

## Trigger

A user no longer wants an event's own reminder.

## Outcome

The event follows the user's calendar rule or default again.
