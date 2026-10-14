---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: The scheduled sync comes round
  kind: condition
  unattended: true
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product's access is refused by the provider
  kind: product
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product marks the account as needing reconnecting
  kind: product
  entities: [{entity: connected-account, effect: changes, from: Connected, to: Needs reconnecting, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# A provider stops accepting Musubi's access

## Trigger

A provider refuses the stored access during a sync.

## Outcome

The account and its calendars show they need reconnecting, to the account's owner only.
