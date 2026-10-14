---
kind: primary
routes:
  mobile: Mobile
steps:
- text: The User drags a calendar to a new place in the list
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Name]}]
  contexts:
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product saves the order to the account
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Calendar order]}]
  contexts:
    mobile: {place: 'mobile::signed-in::calendars'}
---

# Reorder calendars

## Trigger

A user wants the calendars they use most at the top.

## Outcome

Calendars appear in the new order in lists and the filter bar.
