---
kind: alternative
routes:
  mobile: Mobile
steps:
- text: The User chooses Delete on a synced calendar and confirms twice, the first time that it is deleted at the provider too
  kind: actor
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Provider]}]
  contexts:
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product deletes it at the provider first
  kind: product
  actor: user
  entities: [{entity: calendar, effect: reads, facts: [Provider]}]
  contexts:
    mobile: {place: 'mobile::signed-in::calendar-settings'}
- text: The Product deletes the calendar and what is homed in it in Musubi
  kind: product
  actor: user
  entities: [{entity: calendar, effect: removes}, {entity: calendar-membership, effect: removes, with: calendar}, {entity: invite-link, effect: removes, with: calendar}, {entity: event, effect: removes, from: Scheduled, with: calendar}, {entity: task, effect: removes, with: calendar}]
  contexts:
    mobile: {place: 'mobile::signed-in::calendar-settings'}
---

# Delete a synced calendar from the phone

## Trigger

The person whose account a synced calendar comes from deletes it in the phone app.

## Outcome

The calendar is deleted at the provider and then in Musubi; if the provider refuses, nothing is deleted.

## Edge cases

- The web offers Stop syncing for synced calendars instead of deleting them.
