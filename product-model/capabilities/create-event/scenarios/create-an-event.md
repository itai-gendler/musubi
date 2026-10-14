---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters a title, start and end or all day, and optionally a repeat, location, link, description and whether attendance is allowed
  kind: actor
  actor: user
  entities: [{entity: attendance, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The User chooses the calendars, marking one as home
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The user is an owner or editor of each chosen calendar and the end is after the start
  kind: condition
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product creates the event with the user as organizer and shows it to the members of each calendar
  kind: product
  actor: user
  entities: [{entity: event, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars]}, {entity: attendance, effect: creates, facts: [Answer], with: event}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Create an event

## Trigger

A user taps or drags on the grid, or opens the composer.

## Outcome

The event appears in the chosen calendars for every member, with the first chosen calendar as its home.

## Edge cases

- Allow attendance is off unless chosen; the creator is entered as Going either way, which shows once attendance is allowed.
- A reminder chosen in the phone composer is saved as the user's own reminder for the event.
