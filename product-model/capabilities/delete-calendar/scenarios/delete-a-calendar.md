---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Delete calendar and confirms
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: It is not the user's personal calendar
  kind: condition
  entities: [{entity: calendar, effect: reads, facts: [Personal]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product deletes the calendar, its memberships and invite links, and the events and tasks homed in it, everywhere
  kind: product
  actor: user
  entities: [{entity: calendar, effect: removes}, {entity: calendar-membership, effect: removes, with: calendar}, {entity: invite-link, effect: removes, with: calendar}, {entity: event, effect: removes, from: Scheduled, with: calendar}, {entity: task, effect: removes, with: calendar}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product removes the calendar from every member's devices
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar-settings'}
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Delete a calendar

## Trigger

An owner no longer needs a calendar.

## Outcome

The calendar is gone for every member, with the events and tasks homed in it.

## Edge cases

- Events and tasks merely linked into the calendar keep their home and stay in their other calendars.
- Deleted events disappear from offline devices at their next refresh.
