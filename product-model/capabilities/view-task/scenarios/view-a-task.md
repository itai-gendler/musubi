---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens a task
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product shows the task and the calendars of it the user can see
  kind: product
  actor: user
  entities: [{entity: task, effect: reads, facts: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Related task, Completed at, Home calendar, Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# View a task

## Trigger

A user wants the details of a task.

## Outcome

The task's details show, with only the actions its home calendar allows the user.
