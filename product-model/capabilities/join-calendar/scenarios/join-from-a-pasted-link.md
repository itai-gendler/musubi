---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User pastes the link they were given under Join a shared calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product previews the calendar it opens
  kind: product
  actor: user
  entities: [{entity: invite-link, effect: reads, facts: [Expires, Uses]}, {entity: calendar, effect: reads, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The User chooses to join
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product makes the user a viewer and counts the use
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: creates, facts: [Role]}, {entity: invite-link, effect: changes, facts: [Uses]}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
---

# Join from a pasted invite link

## Trigger

A user was given an invite link as text.

## Outcome

The pasted link's calendar is previewed and joined as from the link itself.
