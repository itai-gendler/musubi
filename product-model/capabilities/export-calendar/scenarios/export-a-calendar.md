---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses a calendar to export
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product produces the calendar's events as an iCalendar file
  kind: product
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name]}, {entity: event, effect: reads, facts: [Title, Starts, Ends, All day, Repeat, Location, Description]}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Export a calendar

## Trigger

A member wants a copy of a calendar to keep or move.

## Outcome

An .ics file named after the calendar is downloaded or shared.
