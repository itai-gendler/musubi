---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Leave calendar and confirms
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product removes the user's membership and drops the calendar from their devices
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: removes}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Leave a calendar

## Trigger

A member no longer wants a shared calendar.

## Outcome

They are no longer a member and need a new invitation to come back.
