---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a reminder option for the calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product saves the rule on the user's membership
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: changes, facts: [Reminder]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Set a reminder rule for a calendar

## Trigger

A member wants a calendar's events to remind them differently, or never.

## Outcome

Events of that calendar remind this member by the new rule unless an event has its own choice.

## Edge cases

- Joining a calendar full of birthdays takes one decision here rather than one per event.
