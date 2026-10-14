---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Sign out
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product ends the session and clears what this device kept of the account
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::settings'}
---

# Sign out

## Trigger

A user is done on this device.

## Outcome

They are signed out on this device.
