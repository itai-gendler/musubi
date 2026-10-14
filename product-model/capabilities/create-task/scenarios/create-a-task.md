---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters a title and optionally notes, status, priority, start, due, repeat and link, and chooses a calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Supports tasks]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The user is an owner or editor of the calendar and it keeps tasks
  kind: condition
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}, {entity: calendar, effect: reads, facts: [Supports tasks]}, {entity: user, effect: reads, facts: []}, {entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product creates the task with that calendar as its home
  kind: product
  actor: user
  entities: [{entity: task, effect: creates, facts: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Home calendar, Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Create a task

## Trigger

A user has something to do.

## Outcome

The task exists in the chosen calendar for its members.

## Edge cases

- Only calendars that keep tasks and that the user edits are offered.
- A repeat needs a start or due date first.
- A Google Tasks list keeps due dates as days, without a time.
