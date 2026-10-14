---
kind: validation
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User enters a CalDAV server and credentials
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
- text: The Product cannot reach the calendars with them and connects nothing
  kind: product
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::connections'}
    mobile: {place: 'mobile::signed-in::connect-calendars'}
---

# Refuse wrong CalDAV credentials

## Trigger

The server address or credentials do not work.

## Outcome

Nothing is connected and the user is told to check them, and that iCloud needs an app-specific password.

## Edge cases

- Accepted credentials whose first sync fails are reported as such, so the user can retry.
