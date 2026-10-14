---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User changes the theme, opening view, week start, time or date format, default reminders or whether changes are emailed
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::general-settings'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product saves the settings to the account
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Theme, Default view, Week starts on, Time format, Date format, Default reminder, Event change emails]}]
  contexts:
    web: {place: 'web::signed-in::general-settings'}
    mobile: {place: 'mobile::signed-in::settings'}
---

# Change general settings

## Trigger

A user wants Musubi to suit them.

## Outcome

The change applies at once and on their other devices.

## Edge cases

- The phone also offers tab labels; the web keeps how details open in this browser only.
