---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a different reminder option
  kind: actor
  actor: user
  entities: [{entity: event-reminder, effect: reads, facts: [Reminder]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product saves the new choice
  kind: product
  actor: user
  entities: [{entity: event-reminder, effect: changes, facts: [Reminder]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Change an event's own reminder

## Trigger

A user already has a reminder of their own on an event and picks another.

## Outcome

The event reminds them by the new choice.
