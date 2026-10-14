---
kind: edge
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User creates a calendar at a connected account
  kind: actor
  actor: user
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product reports that the provider rejected the new calendar and creates nothing
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
---

# Provider refuses the new calendar

## Trigger

The provider rejects creating the calendar, or the account no longer grants calendar writes.

## Outcome

No calendar is created in Musubi and the provider's reason is shown.
