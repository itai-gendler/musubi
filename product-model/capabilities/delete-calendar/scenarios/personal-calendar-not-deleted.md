---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens the settings of their personal calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The calendar is the user's personal calendar
  kind: condition
  entities: [{entity: calendar, effect: reads, facts: [Personal]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product offers no Delete calendar
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Keep the personal calendar

## Trigger

A user looks to delete their personal calendar.

## Outcome

Deleting is not offered, and the server refuses it.
