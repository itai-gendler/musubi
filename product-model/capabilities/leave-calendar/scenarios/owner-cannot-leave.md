---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens a calendar they own
  kind: actor
  actor: user
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product offers no Leave calendar, and the server refuses it
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Keep the owner in their calendar

## Trigger

The owner looks to leave their own calendar.

## Outcome

Leaving is not offered; the owner hands the calendar over or deletes it instead.
