---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a different answer
  kind: actor
  actor: user
  entities: [{entity: attendance, effect: reads, facts: [Answer]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product records the new answer
  kind: product
  actor: user
  entities: [{entity: attendance, effect: changes, facts: [Answer]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Change an answer

## Trigger

A user's plans change.

## Outcome

The new answer replaces the old one.

## Edge cases

- Declining also stops the event's reminders and change emails for the user.
