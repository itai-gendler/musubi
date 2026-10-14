---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses to revoke a link
  kind: actor
  actor: user
  entities: [{entity: invite-link, effect: reads, facts: [Expires, Uses]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::invite-links'}
- text: The Product deletes the invite link
  kind: product
  actor: user
  entities: [{entity: invite-link, effect: removes}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::invite-links'}
---

# Revoke an invite link

## Trigger

A link reached people it should not have.

## Outcome

The link no longer opens the calendar; people who already joined stay members.
