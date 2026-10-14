---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a view and moves to the period they want
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The User shows or hides calendars, or on the web switches to another of their views
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product shows the events and dated tasks of the shown calendars, repeating events expanded for the period
  kind: product
  actor: user
  entities: [{entity: event, effect: reads, facts: [Title, Starts, Ends, All day, Color]}, {entity: task, effect: reads, facts: [Title, Status, Due]}, {entity: calendar, effect: reads, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# Browse the calendar

## Trigger

A user wants to see what is coming up.

## Outcome

The chosen period is shown with every visible event and dated task, coloured by calendar.

## Edge cases

- On the web, a page decides the view, the calendars shown and which of events, tasks and meetings appear.
- What was last loaded stays readable offline; changes are refused until the server answers again.
- Changes others make arrive live; a missed one arrives at the next refresh.
