---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User changes the event's details and saves
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The user is an owner or editor of the event's home calendar
  kind: condition
  entities: [{entity: event, effect: reads, facts: [Home calendar]}, {entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product saves the change and updates it in every linked calendar
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Edit an event

## Trigger

Something about an event changes.

## Outcome

The event is changed for every member of every calendar it is in.

## Edge cases

- Leaving the editor with unsaved changes asks whether to discard them.
