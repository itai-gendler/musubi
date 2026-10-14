---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks Editor or Viewer for a member
  kind: actor
  actor: user
  entities: [{entity: calendar-membership, effect: reads, facts: [Role]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
- text: The Product changes the member's role and tells their devices
  kind: product
  actor: user
  entities: [{entity: calendar-membership, effect: changes, facts: [Role]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
---

# Change a member's role

## Trigger

An owner wants someone to edit, or only to see, a calendar.

## Outcome

The member is now an editor or a viewer and can or cannot add and change what is homed there.
