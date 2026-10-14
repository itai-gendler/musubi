---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Delete and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The user is an owner or editor of the task's home calendar
  kind: condition
  entities: [{entity: task, effect: reads, facts: [Home calendar]}, {entity: calendar-membership, effect: reads, facts: [Role]}, {entity: user, effect: reads, facts: []}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product deletes the task everywhere
  kind: product
  actor: user
  entities: [{entity: task, effect: removes}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Delete a task

## Trigger

A task is no longer needed.

## Outcome

The task is gone from every calendar it was in.
