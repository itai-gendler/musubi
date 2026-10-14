---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a picture
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: It is a JPEG, PNG or WebP image of at most 256 KB
  kind: condition
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product stores the photo and shows it beside the user's name
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Photo]}]
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
---

# Change the profile photo

## Trigger

A user picks a picture of themselves.

## Outcome

The new photo shows wherever their name does.
