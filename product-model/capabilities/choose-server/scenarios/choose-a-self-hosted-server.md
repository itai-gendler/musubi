---
kind: primary
routes:
  mobile: Mobile
steps:
- text: The Visitor enters their server's address on the welcome screen
  kind: actor
  actor: visitor
  entities: []
  contexts:
    mobile: {place: 'mobile::visitor::welcome'}
- text: The Product checks the server answers and uses it for signing in and syncing
  kind: product
  entities: []
  contexts:
    mobile: {place: 'mobile::visitor::welcome'}
---

# Point the app at another server

## Trigger

Someone runs Musubi themselves.

## Outcome

The app signs in and syncs against that server from then on.

## Edge cases

- A phone on the same network as a development server needs the server's network address, not localhost.
