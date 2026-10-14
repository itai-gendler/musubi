---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: 'The User removes a calendar that is not the home from the event: Unlink on the phone, unticking it in the web editor'
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: [Home calendar, Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product takes the event out of that calendar
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Unlink an event from a calendar

## Trigger

An event no longer belongs in one of the calendars it is linked into.

## Outcome

The event is gone from that calendar and still in the rest.

## Edge cases

- The home calendar is never offered: taking the event out of its home is deleting it.
