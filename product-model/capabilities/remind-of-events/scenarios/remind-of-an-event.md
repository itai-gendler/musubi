---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: A reminder time arrives for an event the person can see
  kind: condition
  unattended: true
  entities: [{entity: event, effect: reads, facts: [Title, Starts, All day]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product works out the person's rule from their event reminder, calendar rules in their order and default
  kind: product
  entities: [{entity: event-reminder, effect: reads, facts: [Reminder]}, {entity: calendar-membership, effect: reads, facts: [Reminder]}, {entity: user, effect: reads, facts: [Calendar order, Default reminder, Time zone]}, {entity: calendar, effect: reads, facts: []}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product shows a notification for the event
  kind: product
  entities: [{entity: event, effect: reads, facts: [Title, Starts]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# Remind of an event

## Trigger

An event's reminder time arrives for a person.

## Outcome

A notification names the event and when it starts.

## Edge cases

- An all-day event reminds at a time of day on a day before, in the person's own time zone.
- The browser asks for permission to notify where a reminder is being turned on, not at launch.
