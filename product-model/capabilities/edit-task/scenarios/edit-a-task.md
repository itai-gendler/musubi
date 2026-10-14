---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User changes the task and saves
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The user is an owner or editor of the task's home calendar
  kind: condition
  entities: [{entity: task, effect: reads, facts: [Home calendar]}, {entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product saves the change everywhere the task is linked
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Title, Notes, Starts, Due, All day, Priority, Repeat, Link]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Edit a task

## Trigger

Something about a task changes.

## Outcome

The task is changed in every calendar it is in.
