---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User changes the name or colour of a synced calendar and saves
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product makes the change at the provider first
  kind: product
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product saves the calendar in Musubi
  kind: product
  actor: user
  entities: [{entity: calendar, effect: changes, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Rename a synced calendar

## Trigger

The person whose account a synced calendar comes from renames it.

## Outcome

The calendar is renamed at the provider and in Musubi; if the provider rejects it, nothing changes.

## Edge cases

- An Outlook account's own default calendar keeps its name and colour; the phone does not offer editing it.
