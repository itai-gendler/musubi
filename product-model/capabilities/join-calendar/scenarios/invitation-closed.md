---
kind: validation
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
- text: The link is expired, used up or revoked
  kind: condition
  entities: [{entity: invite-link, effect: reads, facts: [Expires, People limit, Uses]}]
  contexts:
    web: {place: 'web::signed-in::invitation'}
    mobile: {place: 'mobile::signed-in::invitation'}
- text: The Product says the invitation is closed
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::invitation'}
    mobile: {place: 'mobile::signed-in::invitation'}
---

# Refuse a closed invitation

## Trigger

The link has expired, reached its people limit or was revoked.

## Outcome

The page says the invitation is closed and to ask for a fresh link.
