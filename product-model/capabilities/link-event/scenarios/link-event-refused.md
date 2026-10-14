---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens Link to another calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The user only views the other calendars, or the event is in all of them
  kind: condition
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}, {entity: event, effect: reads, facts: [Calendars]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product offers no calendar to link to
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Offer only calendars the user edits

## Trigger

A user looks to link an event.

## Outcome

Only calendars the user owns or edits, and the event is not in yet, are offered.
