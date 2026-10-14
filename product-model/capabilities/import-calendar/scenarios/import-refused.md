---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User picks a file Musubi cannot import
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
- text: The Product refuses the import and creates no calendar
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::calendars-settings'}
    mobile: {place: 'mobile::signed-in::calendars'}
---

# Refuse an unusable file

## Trigger

The file is not valid iCalendar, has unsupported recurrence dates or more than 10,000 events.

## Outcome

Nothing is created.

## Edge cases

- Importing repeating events into an Outlook account is refused before anything is created.
