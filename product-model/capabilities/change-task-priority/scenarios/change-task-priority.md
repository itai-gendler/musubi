---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a priority
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product saves the priority
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Priority]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Change a task's priority

## Trigger

A task becomes more or less pressing.

## Outcome

The task shows its new priority everywhere.
