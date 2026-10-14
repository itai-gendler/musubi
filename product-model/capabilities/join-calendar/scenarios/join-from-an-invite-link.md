---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User opens the invitation they were sent
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::invitation'}
    mobile: {place: 'mobile::signed-in::invitation'}
- text: The Product shows the calendar's name, who shared it, its members and its events of the next 30 days
  kind: product
  actor: user
  entities: [{entity: invite-link, effect: reads, facts: [Expires, People limit, Uses]}, {entity: calendar, effect: reads, facts: [Name, Color]}, {entity: user, effect: reads, facts: [Name, Photo]}, {entity: event, effect: reads, facts: [Title, Starts, Ends, All day]}]
  contexts:
    web: {place: 'web::signed-in::invitation'}
    mobile: {place: 'mobile::signed-in::invitation'}
- text: The User chooses to join
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::invitation'}
    mobile: {place: 'mobile::signed-in::invitation'}
- text: The Product makes the user a viewer of the calendar and counts the use
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: creates, facts: [Role]}, {entity: invite-link, effect: changes, facts: [Uses]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::invitation'}
    mobile: {place: 'mobile::signed-in::invitation'}
---

# Join from an invite link

## Trigger

A signed-in user opens an invite link someone sent.

## Outcome

They are a viewer of the calendar and it opens in their calendar view.

## Edge cases

- Someone who is already a member joins nothing new and uses up nothing.
