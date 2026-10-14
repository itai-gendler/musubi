---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Delete on an event and confirms
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The user cannot edit the event's home calendar but edits some of its other calendars
  kind: condition
  entities: [{entity: event, effect: reads, facts: [Home calendar, Calendars]}, {entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product takes the event out of the calendars the user edits
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Delete an event without rights on its home

## Trigger

A user who edits some of the calendars an event is linked into, but not its home, deletes it.

## Outcome

The event leaves the calendars the user edits and stays in the others, home included.
