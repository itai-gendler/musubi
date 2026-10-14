---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens an event
  kind: actor
  actor: user
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product shows the event, the calendars of it the user can see, the attendees' answers and the user's reminder
  kind: product
  actor: user
  entities: [{entity: event, effect: reads, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars]}, {entity: attendance, effect: reads, facts: [Answer]}, {entity: event-reminder, effect: reads, facts: [Reminder]}, {entity: calendar, effect: reads, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# View an event

## Trigger

A user wants the details of an event.

## Outcome

The details show, with only the actions the user's role on its home calendar allows.

## Edge cases

- Attendees show by name and photo only, never by email address.
- An event the user cannot change says it is view only.
