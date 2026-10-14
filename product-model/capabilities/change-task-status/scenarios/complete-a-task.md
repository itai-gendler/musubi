---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User sets the task to Completed
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::tasks'}
- text: The Product completes the task and records when
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Status, Completed at]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::tasks'}
---

# Complete a task

## Trigger

A user finishes a task.

## Outcome

The task is completed, with the time it was completed, in every calendar it is in.
