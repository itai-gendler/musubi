---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User creates a task in a synced task list
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Provider]}, {entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product saves the task and a delivery to the provider together
  kind: product
  actor: user
  entities: [{entity: task, effect: creates, facts: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Home calendar, Calendars]}, {entity: delivery, effect: creates, to: Pending, facts: [Destination, Operation], with: task}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Create a task in a synced task list

## Trigger

A user creates a task in a Google Tasks, Microsoft To Do or CalDAV task list.

## Outcome

The task is saved and shows at once; its delivery to the provider follows.
