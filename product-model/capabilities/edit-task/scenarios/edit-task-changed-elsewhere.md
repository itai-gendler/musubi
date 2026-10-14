---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User saves changes to a task
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The task or its provider access changed since the user opened it
  kind: condition
  entities: [{entity: task, effect: reads, facts: [Title, Notes, Starts, Due, All day, Priority, Repeat, Link]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product refuses the save and says to refresh
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Refuse an edit to a task that changed meanwhile

## Trigger

Someone else saved the task, or its provider access changed, after the user opened it.

## Outcome

Nothing is saved; the draft is kept so the user can refresh and try again.

## Edge cases

- An app too old for the current task saving is told to update Musubi and keeps the draft.
