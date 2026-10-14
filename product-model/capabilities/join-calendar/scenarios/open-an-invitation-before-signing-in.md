---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor opens the invitation they were sent in a browser
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::invitation'}
- text: The Product shows the calendar's name, who shared it, its members and its next 30 days
  kind: product
  actor: visitor
  entities: [{entity: invite-link, effect: reads, facts: [Expires, Uses]}, {entity: calendar, effect: reads, facts: [Name, Color]}, {entity: user, effect: reads, facts: [Name, Photo]}, {entity: event, effect: reads, facts: [Title, Starts, Ends, All day]}]
  contexts:
    web: {place: 'web::visitor::invitation'}
- text: The Visitor chooses Sign in
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::invitation'}
---

# Open an invitation before signing in

## Trigger

Someone who is not signed in opens an invite link in a browser.

## Outcome

They see the preview; signing in brings them back to the same invitation to join.

## Edge cases

- On the phone, an invite link opened before signing in waits until the person has signed in.
