---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens Tasks and, on the web, picks List or Kanban
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::tasks'}
    mobile: {place: 'mobile::signed-in::tasks'}
- text: The Product lists each task the user can see once
  kind: product
  actor: user
  entities: [{entity: task, effect: reads, facts: [Title, Status, Due, Priority, Repeat]}]
  contexts:
    web: {place: 'web::signed-in::tasks'}
    mobile: {place: 'mobile::signed-in::tasks'}
---

# Browse tasks

## Trigger

A user wants to see what there is to do.

## Outcome

Their tasks are listed with status, due date, priority and repeat.

## Edge cases

- A task only shows the calendars of it the user can see.
- Tasks with dates also appear in the calendar views.
