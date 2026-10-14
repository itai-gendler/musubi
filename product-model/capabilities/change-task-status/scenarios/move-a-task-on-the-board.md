---
kind: alternative
routes:
  web: Web
steps:
- text: The User drags a task to another column of the board
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::tasks'}
- text: The Product sets the task's status to that column's
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Status, Completed at]}]
  contexts:
    web: {place: 'web::signed-in::tasks'}
---

# Move a task to another column

## Trigger

On the web board a user drags a task to another status column.

## Outcome

The task has the status of the column it was dropped in.

## Edge cases

- Tasks the user cannot change show as read only and cannot be dragged.
