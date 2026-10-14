---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Stop syncing, Disconnect on the phone, and confirms
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product removes the synced calendar and its events from Musubi and remembers not to bring it back
  kind: product
  actor: user
  entities: [{entity: calendar, effect: removes}, {entity: calendar-membership, effect: removes, with: calendar}, {entity: event, effect: removes, from: Scheduled, with: calendar}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Stop syncing a calendar

## Trigger

A connected account brings in a calendar the user does not want in Musubi, such as holidays.

## Outcome

The calendar and its events are gone from Musubi and remain at the provider.

## Edge cases

- It is the only way to remove a read-only synced calendar, which cannot be deleted.
