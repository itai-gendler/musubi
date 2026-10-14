---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User confirms their name and, on the phone, adds a photo
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::onboarding'}
    mobile: {place: 'mobile::signed-in::onboarding'}
- text: The Product saves the name
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Name]}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
    mobile: {place: 'mobile::signed-in::onboarding'}
- text: The User names and colours their personal calendar
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
    mobile: {place: 'mobile::signed-in::onboarding'}
- text: The Product renames the personal calendar
  kind: product
  actor: user
  entities: [{entity: calendar, effect: changes, facts: [Name, Color]}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
    mobile: {place: 'mobile::signed-in::onboarding'}
- text: The User skips connecting other calendars and finishes
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
    mobile: {place: 'mobile::signed-in::onboarding'}
- text: The Product records that set-up is done
  kind: product
  actor: user
  entities: [{entity: user, effect: changes, facts: [Set up]}]
  contexts:
    web: {place: 'web::signed-in::onboarding'}
    mobile: {place: 'mobile::signed-in::onboarding'}
---

# Complete the first-run set-up

## Trigger

A user who has not finished set-up opens Musubi.

## Outcome

Set-up is finished on every device and the calendar opens.

## Edge cases

- Connecting Google or Outlook from the last step finishes set-up first, then goes to the provider (Connect calendar account).
- The phone's last step also offers creating a calendar to share and its invite link.
