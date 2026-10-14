---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The Visitor chooses Continue with Google, Microsoft or Apple, among those the server offers
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::welcome'}
- text: The Visitor approves at the provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::welcome'}
- text: The Product signs the person in to the account with that address
  kind: product
  actor: visitor
  entities: [{entity: user, effect: reads, facts: [Email]}]
  contexts:
    web: {place: 'web::visitor::sign-in'}
    mobile: {place: 'mobile::visitor::welcome'}
---

# Sign in with Google, Microsoft or Apple

## Trigger

A person prefers to sign in with an account they already have.

## Outcome

They are signed in; an address with no Musubi account gets a new account with its personal calendar and first page.

## Edge cases

- A server with no provider credentials offers no provider buttons.
- When the provider does not come back, the sign-in page says so and offers the passphrase instead.
