---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Make an independent copy and picks a calendar they edit that can hold it
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Supports tasks]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product creates a new task from the original with that calendar as its home
  kind: product
  actor: user
  entities: [{entity: task, as: original, effect: reads, facts: [Title, Notes, Starts, Due, All day, Priority, Repeat, Link]}, {entity: task, as: copy, effect: creates, facts: [Title, Notes, Status, Starts, Due, All day, Priority, Repeat, Link, Home calendar, Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Make an independent copy of a task

## Trigger

A user wants their own version of a task, or the destination cannot keep a live link.

## Outcome

A new task, homed in the chosen calendar, starts as a copy of the original.

## Edge cases

- If the copy request is interrupted, repeating it recovers the copy already made rather than making another.
