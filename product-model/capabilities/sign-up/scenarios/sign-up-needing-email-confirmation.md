---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor enters their name, email and a passphrase
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The server requires email confirmation
  kind: condition
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The Product creates the user unconfirmed, with their personal calendar and first page
  kind: product
  actor: visitor
  entities: [{entity: user, effect: creates, facts: [Name, Email, Email confirmed, Passphrase, Theme, Default view, Week starts on, Time format, Date format, Default reminder, Event change emails, Set up]}, {entity: calendar, effect: creates, facts: [Name, Color, Personal, Supports tasks, Live task links], with: user}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}, {entity: page, effect: creates, facts: [Name, View, Item types, Calendars shown, Default, Position], with: user}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The Product emails a confirmation link to the address and says to look for it
  kind: product
  entities: [{entity: user, effect: reads, facts: [Email]}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
---

# Create an account on a server that requires confirmation

## Trigger

A visitor signs up on a server whose operator requires confirmed email addresses.

## Outcome

The account exists but cannot sign in yet; a confirmation link valid for one hour is on its way.
