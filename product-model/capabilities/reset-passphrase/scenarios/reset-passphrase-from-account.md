---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Reset passphrase in Account
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
- text: The Product emails a reset link to the user's address
  kind: product
  actor: user
  entities: [{entity: user, effect: reads, facts: [Email, Name]}]
  contexts:
    web: {place: 'web::signed-in::account'}
- text: The Visitor opens the link and enters a new passphrase
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::reset-passphrase'}
- text: The Product replaces the passphrase
  kind: product
  actor: visitor
  entities: [{entity: user, effect: changes, facts: [Passphrase]}]
  contexts:
    web: {place: 'web::visitor::reset-passphrase'}
---

# Reset the passphrase from the account

## Trigger

A signed-in user wants a new passphrase.

## Outcome

A reset link goes to their own address; following it sets the new passphrase.
