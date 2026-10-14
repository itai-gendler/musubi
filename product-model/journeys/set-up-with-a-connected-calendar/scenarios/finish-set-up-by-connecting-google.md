---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User confirms their name and their personal calendar's name and colour
  kind: actor
  actor: user
  capability: complete-onboarding
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
- text: The Product saves them
  kind: product
  actor: user
  capability: complete-onboarding
  entities: [{entity: user, effect: changes, facts: [Name]}, {entity: calendar, effect: changes, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
- text: The User chooses Connect Google Calendar on the last step
  kind: actor
  actor: user
  capability: complete-onboarding
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
- text: The Product records that set-up is done and takes the user to Google
  kind: product
  actor: user
  capability: complete-onboarding
  entities: [{entity: user, effect: changes, facts: [Set up]}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
- text: The User approves Musubi's access at Google
  kind: actor
  actor: user
  capability: connect-calendar-account
  entities: []
  contexts:
    web: {place: 'web::signed-in'}
- text: The Product connects the account and brings in its calendars and their events
  kind: product
  actor: user
  capability: connect-calendar-account
  entities: [{entity: connected-account, effect: creates, to: Connected, facts: [Provider, Account name, Includes tasks]}, {entity: calendar, effect: creates, facts: [Name, Color, Personal, Provider, Supports tasks, Live task links], with: connected-account}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}, {entity: event, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Color, Home calendar, Calendars], with: calendar}]
  contexts:
    web: {place: 'web::signed-in'}
---

# Finish set-up by connecting Google

## Trigger

A new user reaches the last step of set-up and wants their Google calendars in Musubi.

## Outcome

Set-up is finished, the Google account is connected and its calendars appear in Musubi.
