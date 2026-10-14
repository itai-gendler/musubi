---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: A reminder time arrives
  kind: condition
  unattended: true
  entities: [{entity: event, effect: reads, facts: [Title]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The person declined the event, or it is cancelled
  kind: condition
  entities: [{entity: attendance, effect: reads, facts: [Answer]}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product shows nothing
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# Stay silent for declined and cancelled events

## Trigger

A reminder time arrives for an event the person declined, or one that is cancelled.

## Outcome

No notification is shown.
