---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks an .ics file and a name and colour for the new calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The file is valid iCalendar with at most 10,000 events
  kind: condition
  entities: [{entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product creates the calendar and an event for each one in the file
  kind: product
  actor: user
  entities: [{entity: calendar, effect: creates, facts: [Name, Color, Personal, Supports tasks, Live task links]}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}, {entity: event, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Allow attendance, Color, Home calendar, Calendars], with: calendar}, {entity: attendance, effect: creates, facts: [Answer], with: event}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
---

# Import an .ics file

## Trigger

A user has a calendar exported from elsewhere.

## Outcome

A new calendar holds the file's events; the user is its owner.

## Edge cases

- Without a chosen name, the calendar takes the file's own name, or Imported calendar.
