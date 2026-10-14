---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses to remove the task from a calendar that is not its home, and confirms
  kind: actor
  actor: user
  entities: [{entity: task, effect: reads, facts: [Home calendar, Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product takes the task out of that calendar
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Remove a task from a calendar

## Trigger

A task no longer belongs in one of the calendars it is linked into.

## Outcome

The task is gone from that calendar and still in the rest; a synced destination gets a delete.

## Edge cases

- An older Microsoft To Do link shows as Unsupported link; the item stays in To Do after removing it.
