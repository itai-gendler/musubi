---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses to make a member the owner and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
- text: The calendar is neither the user's personal calendar nor synced from a provider
  kind: condition
  entities: [{entity: calendar, effect: reads, facts: [Personal, Provider]}, {entity: user, effect: reads, facts: []}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
- text: The Product makes that member the owner and the user an editor
  kind: product
  actor: user
  entities: [{entity: calendar, effect: changes, facts: []}, {entity: calendar-membership, as: new-owner, effect: changes, facts: [Role]}, {entity: calendar-membership, as: previous-owner, effect: changes, facts: [Role]}]
  contexts:
    web: {place: 'web::signed-in::sharing'}
    mobile: {place: 'mobile::signed-in::members'}
---

# Transfer ownership

## Trigger

An owner wants someone else to run a calendar.

## Outcome

The chosen member is the owner and the previous owner an editor, on every device.
