---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Link to another calendar, Share on the phone, and picks a calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name, Live task links]}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The user edits that calendar and it keeps live task links
  kind: condition
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}, {entity: calendar, effect: reads, facts: [Live task links]}, {entity: user, effect: reads, facts: []}, {entity: task, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
- text: The Product adds the calendar to the task
  kind: product
  actor: user
  entities: [{entity: task, effect: changes, facts: [Calendars]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::task'}
    mobile: {place: 'mobile::signed-in::task'}
---

# Link a task to another calendar

## Trigger

A user wants a task to show in another calendar too.

## Outcome

The same task is in the other calendar; its home still decides who changes and completes it.

## Edge cases

- Editing rights on the destination let its members see the task, not change or complete it.
- A repeating task is linked only into Musubi calendars.
