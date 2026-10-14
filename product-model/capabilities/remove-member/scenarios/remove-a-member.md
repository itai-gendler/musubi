---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses to remove a member
  kind: actor
  actor: user
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
- text: The Product removes the membership and drops the calendar from that person's devices
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: removes}, {entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
---

# Remove a member

## Trigger

Someone should no longer see a calendar.

## Outcome

They are no longer a member; events and tasks they can see only through it go away for them.

## Edge cases

- The owner is never offered for removal.
