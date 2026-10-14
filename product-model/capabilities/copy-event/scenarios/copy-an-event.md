---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Make a copy, Fork on the phone, and picks a calendar they edit
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The original is not already in that calendar
  kind: condition
  entities: [{entity: event, as: original, effect: reads, facts: [Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product creates a new event from the original with that calendar as its home
  kind: product
  actor: user
  entities: [{entity: event, as: original, effect: reads, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance]}, {entity: event, as: copy, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars]}, {entity: attendance, effect: creates, facts: [Answer], with: copy}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Make an independent copy of an event

## Trigger

A user wants their own version of an event to change freely.

## Outcome

A new event, homed in the chosen calendar, starts as a copy of the original.
