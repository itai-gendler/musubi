---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters a name and colour and chooses one of their connected accounts
  kind: actor
  actor: user
  entities: [{entity: connected-account, effect: reads, facts: [Provider, Account name]}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product creates the calendar at the provider first
  kind: product
  actor: user
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product adds it as a synced calendar the user owns
  kind: product
  actor: user
  entities: [{entity: calendar, effect: creates, facts: [Name, Color, Personal, Supports tasks, Live task links, Provider]}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
---

# Create a calendar at a connected account

## Trigger

A user wants the new calendar to live at Google, Outlook or a CalDAV server.

## Outcome

The calendar exists at the provider and as a synced calendar the user owns in Musubi.
