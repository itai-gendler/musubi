---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User sets how many days the link lasts and how many people may use it, or leaves them open
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::invite-links'}
- text: The Product creates the invite link
  kind: product
  actor: user
  entities: [{entity: invite-link, effect: creates, facts: [Expires, People limit, Uses]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::invite-links'}
---

# Create an invite link

## Trigger

A member wants to bring people into a calendar.

## Outcome

A new link is listed, ready to copy or share.

## Edge cases

- On the web a new link lasts 7 days unless the days are changed or cleared.
