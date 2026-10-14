---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks Needs action, In progress or Cancelled
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product sets the status, clearing the completion time when it was completed
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Status, Completed at]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Reopen or move a task to another status

## Trigger

A completed task needs more work, or a task starts or is called off.

## Outcome

The task has its new status; reopening clears when it was completed.
