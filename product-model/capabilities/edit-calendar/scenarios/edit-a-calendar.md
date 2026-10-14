---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User changes the name or colour and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product saves the calendar and updates it for every member
  kind: product
  actor: user
  entities: [{entity: calendar, effect: changes, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Rename or recolour a calendar

## Trigger

A calendar's owner wants it called or coloured differently.

## Outcome

The calendar shows its new name and colour to every member.
