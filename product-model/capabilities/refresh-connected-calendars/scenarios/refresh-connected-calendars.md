---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Refresh in Connections
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
- text: The Product syncs each of the user's connected accounts
  kind: product
  actor: user
  entities: [{entity: connected-account, effect: reads, facts: [Provider, Account name]}]
  contexts:
    web: {place: 'web::signed-in::connections'}
---

# Refresh connected calendars

## Trigger

A user just changed something at a provider and wants to see it.

## Outcome

Changes at the providers are in Musubi, or the user is told the sync failed.
