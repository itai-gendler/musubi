---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Link to another calendar and picks one of the calendars they edit
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product adds the calendar to the event and shows it to that calendar's members
  kind: product
  actor: user
  entities: [{entity: event, effect: changes, facts: [Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Link an event to another calendar

## Trigger

A user wants an event to show in another calendar too, such as a dinner in a shared family calendar.

## Outcome

The same event is now in the other calendar for its members.

## Edge cases

- Linking into a synced calendar also queues its creation at the provider.
