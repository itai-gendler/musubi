---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks Default for the calendar's reminder
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product clears the rule on the user's membership
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: changes, facts: [Reminder]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Return a calendar to the default reminder

## Trigger

A member no longer wants a calendar of their own rule.

## Outcome

The calendar's events follow the member's default reminder again.
