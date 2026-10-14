---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User saves an event without a calendar, ending before it starts, or in a calendar they only view
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product refuses and keeps the draft
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Refuse an event that cannot be saved

## Trigger

The event has no calendar, its end is not after its start, or the user cannot edit a chosen calendar.

## Outcome

Nothing is saved and the composer keeps the draft.
