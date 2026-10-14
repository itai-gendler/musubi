---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Disconnect on an account
  kind: actor
  actor: user
  entities: [{entity: connected-account, effect: reads, facts: [Provider, Account name]}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product removes the account and its synced calendars and stops syncing it
  kind: product
  actor: user
  entities: [{entity: connected-account, effect: removes, from: Connected}, {entity: calendar, effect: removes, with: connected-account}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
---

# Disconnect an account

## Trigger

A user no longer wants an account's calendars in Musubi.

## Outcome

The account and its synced calendars are gone from Musubi; the user's other accounts are untouched.

## Edge cases

- An account the user also signs in with stays usable for signing in; only its calendar access ends.
