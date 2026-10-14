---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a reminder option for the event, in its details on the web or its editor on the phone
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The choice differs from what the event would inherit
  kind: condition
  entities: [{entity: calendar-membership, effect: reads, facts: [Reminder]}, {entity: user, effect: reads, facts: [Default reminder]}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product saves the user's reminder for the event
  kind: product
  actor: user
  entities: [{entity: event-reminder, effect: creates, facts: [Reminder]}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Set a reminder for one event

## Trigger

A user wants a particular event to remind them differently.

## Outcome

That event reminds the user by their choice whatever their calendar and default rules say.
