---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a file over 256 KB or not a JPEG, PNG or WebP image
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product refuses it
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
---

# Refuse an unusable photo

## Trigger

A user picks a file that is too large or not a supported image.

## Outcome

The photo stays as it was and the user is told why.
