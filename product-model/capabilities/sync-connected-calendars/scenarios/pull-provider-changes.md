---
kind: primary
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
- text: The Product reads the changes from each connected account
  kind: product
  entities: [{entity: connected-account, effect: reads, facts: [Provider]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product adds new events, updates changed ones and removes those deleted at the provider
  kind: product
  entities: [{entity: event, as: new, effect: creates, to: Scheduled, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description, Color, Home calendar, Calendars]}, {entity: event, as: changed, effect: changes, facts: [Title, Starts, Ends, All day, Repeat, Location, Link, Description]}, {entity: event, as: gone, effect: removes, from: Scheduled}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product marks events the provider called off as cancelled
  kind: product
  entities: [{entity: event, as: called-off, effect: changes, from: Scheduled, to: Cancelled, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product tells members' open devices to refresh when something changed
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# Bring in changes from the providers

## Trigger

The scheduled sync comes round.

## Outcome

Each synced calendar matches its provider, and members' devices refresh.

## Edge cases

- A calendar the user stopped syncing is not brought back.
- A new provider calendar is brought in as one the user owns, or views if it is read-only at the provider.
