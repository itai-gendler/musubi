---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User creates an event in a synced calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Provider]}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product saves the event and a delivery to the provider together
  kind: product
  actor: user
  entities: [{entity: event, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars]}, {entity: attendance, effect: creates, facts: [Answer], with: event}, {entity: delivery, effect: creates, to: Pending, facts: [Destination, Operation], with: event}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Create an event in a synced calendar

## Trigger

A user creates an event in a Google, Outlook or CalDAV calendar.

## Outcome

The event is saved and shows at once; its delivery to the provider follows.

## Edge cases

- Musubi's attendance and reminders stay in Musubi; the provider receives what it can represent.
- A calendar the provider reports as read-only accepts no new events.
