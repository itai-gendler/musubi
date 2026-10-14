---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Delete and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The user is an owner or editor of the event's home calendar
  kind: condition
  entities: [{entity: event, effect: reads, facts: [Home calendar]}, {entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product deletes the event everywhere and drops notices still queued for it
  kind: product
  actor: user
  entities: [{entity: event, effect: removes, from: Scheduled}, {entity: change-notice, effect: removes, from: Queued, with: event}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Delete an event everywhere

## Trigger

An owner or editor of an event's home calendar deletes it.

## Outcome

The event is gone from every calendar it was in, and change emails still waiting for it are dropped.

## Edge cases

- Offline devices learn of the deletion at their next refresh.
