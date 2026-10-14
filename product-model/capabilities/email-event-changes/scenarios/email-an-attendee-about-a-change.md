---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: A queued notice is due
  kind: condition
  unattended: true
  entities: [{entity: change-notice, effect: reads, facts: [Change, Was, Now]}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The attendee has event change emails on
  kind: condition
  entities: [{entity: user, effect: reads, facts: [Event change emails, Email, Time zone]}, {entity: event, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
- text: The Product emails the attendee and marks the notice sent
  kind: product
  entities: [{entity: change-notice, effect: changes, from: Queued, to: Sent, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendar'}
    mobile: {place: 'mobile::signed-in::home'}
---

# Email an attendee about a moved event

## Trigger

A notice for an attendee has waited its few minutes.

## Outcome

The attendee has an email saying the event moved, from when to when, in their own time zone.

## Edge cases

- Changing a description, location or colour sends nothing; only moves and cancellations do.
- Calling a cancellation off sends nothing.
- A server without mail sends no change emails.
