---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens the members of their personal or a synced calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
- text: The calendar is personal or synced from a provider
  kind: condition
  entities: [{entity: calendar, effect: reads, facts: [Personal, Provider]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
- text: The Product offers no ownership transfer
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
---

# Keep personal and synced calendars with their owner

## Trigger

An owner looks to hand over their personal calendar or a synced one.

## Outcome

Ownership transfer is not offered, and the server refuses it.
