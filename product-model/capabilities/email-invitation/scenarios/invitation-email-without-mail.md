---
kind: edge
routes:
  web: Web
steps:
- text: The User sends an invitation by email
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
- text: The server has no mail configured
  kind: condition
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
- text: The Product refuses to send and suggests copying the link
  kind: product
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
---

# Refuse to email without a mail server

## Trigger

The server has no mail configured.

## Outcome

Nothing is sent and the user is told to copy the link instead.
