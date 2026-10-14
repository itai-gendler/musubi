---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters a name and picks a colour
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product creates the calendar with the user as its owner
  kind: product
  actor: user
  entities: [{entity: calendar, effect: creates, facts: [Name, Color, Personal, Supports tasks, Live task links]}, {entity: calendar-membership, effect: creates, facts: [Role], with: calendar}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
---

# Create a Musubi calendar

## Trigger

A user wants a calendar for a project, a family or a team.

## Outcome

The calendar exists with the user as its owner, ready to share.
