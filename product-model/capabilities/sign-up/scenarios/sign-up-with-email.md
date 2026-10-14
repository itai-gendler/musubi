---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor enters their name, email and a passphrase, twice on the phone
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The passphrase has at least 8 characters and no account uses the email
  kind: condition
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The server does not require email confirmation
  kind: condition
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The Product creates the user, a personal calendar named after them that they own, and a first page that shows every calendar
  kind: product
  actor: visitor
  entities: [{entity: user, effect: creates, facts: [Name, Email, Email confirmed, Passphrase, Theme, Default view, Week starts on, Time format, Date format, Default reminder, Event change emails, Set up]}, {entity: calendar, effect: creates, facts: [Name, Color, Personal, Supports tasks, Live task links], with: user}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}, {entity: page, effect: creates, facts: [Name, View, Item types, Calendars shown, Default, Position], with: user}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
- text: The Product signs the new user in
  kind: product
  entities: [{entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::sign-up'}
---

# Create an account with email and passphrase

## Trigger

A visitor wants their own Musubi account.

## Outcome

The account exists with its personal calendar and a page called My calendar, and the person is signed in and taken to the first-run set-up.

## Edge cases

- A Google, Microsoft or Apple sign-in for an address with no account creates the account the same way (Sign in).
