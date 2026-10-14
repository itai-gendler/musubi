---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters the server address, filled in for iCloud, a username and a password, an app-specific one for iCloud
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product checks the credentials, keeps the password encrypted and brings in the account's calendars
  kind: product
  actor: user
  entities: [{entity: connected-account, effect: creates, to: Connected, facts: [Provider, Account name, Server address, Includes tasks]}, {entity: calendar, effect: creates, facts: [Name, Color, Personal, Provider, Supports tasks, Live task links], with: connected-account}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}, {entity: event, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Color, Home calendar, Calendars], with: calendar}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
---

# Connect an iCloud or CalDAV account

## Trigger

A user's calendars live at iCloud or another CalDAV server.

## Outcome

The account is connected and its calendars appear in Musubi.
