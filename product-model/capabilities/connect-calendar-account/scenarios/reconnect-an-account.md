---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses to reconnect the account marked as needing attention
  kind: actor
  actor: user
  entities: [{entity: connected-account, effect: reads, facts: [Provider, Account name]}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The User approves at the provider, or enters the CalDAV password again
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product resumes syncing the account
  kind: product
  actor: user
  entities: [{entity: connected-account, effect: changes, from: Needs reconnecting, to: Connected, facts: []}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
---

# Reconnect an account that needs attention

## Trigger

A connected account stopped accepting Musubi's access.

## Outcome

The account syncs again, with its calendars as they were.
