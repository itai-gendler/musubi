---
kind: primary
routes:
  web: Web
steps:
- text: The User types an email address and sends
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
- text: The Product uses the calendar's newest active invite link, creating one if there is none
  kind: product
  actor: user
  entities: [{entity: invite-link, effect: creates, facts: [Expires, People limit, Uses]}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
- text: The Product emails the link with the inviter's name, the calendar's name and the link's expiry
  kind: product
  actor: user
  entities: [{entity: invite-link, effect: reads, facts: [Expires]}, {entity: calendar, effect: reads, facts: [Name]}, {entity: user, effect: reads, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
---

# Email an invitation

## Trigger

A member wants to invite someone by email rather than pass a link on.

## Outcome

The person receives an email naming who shared which calendar, with the link and how long it lasts.

## Edge cases

- One address is sent at a time, and an account can send at most 20 invitations an hour.
