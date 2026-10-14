---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Google or Outlook and, on the phone, whether to include to-do lists
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The User approves Musubi's access at the provider
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product connects the account and brings in each of its calendars with their events
  kind: product
  actor: user
  entities: [{entity: connected-account, effect: creates, to: Connected, facts: [Provider, Account name, Includes tasks]}, {entity: calendar, effect: creates, facts: [Name, Color, Personal, Provider, Supports tasks, Live task links], with: connected-account}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}, {entity: event, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Color, Home calendar, Calendars], with: calendar}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
---

# Connect a Google or Outlook account

## Trigger

A user wants their existing calendars beside Musubi's.

## Outcome

The account is connected and its calendars appear in Musubi.

## Edge cases

- Several accounts of one provider can be connected; each is separate.
- The web always asks for task access; on the phone it is optional.
- Only providers the server is set up for are offered.
