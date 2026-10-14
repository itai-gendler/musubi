---
kind: primary
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User asks to delete the account and types their exact display name to confirm
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Product emails a deletion link, valid for one hour, to the user's address
  kind: product
  actor: user
  entities: [{entity: user, effect: reads, facts: [Email, Name]}]
  contexts:
    web: {place: 'web::signed-in::account'}
    mobile: {place: 'mobile::signed-in::settings'}
- text: The Visitor opens the link and confirms the deletion
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::visitor::confirm-deletion'}
    mobile: {place: 'web::visitor::confirm-deletion'}
- text: The Product deletes the account with its memberships, owned calendars, the events and tasks it created, its pages, connected accounts, answers and reminders
  kind: product
  actor: visitor
  entities: [{entity: user, effect: removes}, {entity: calendar-membership, effect: removes, with: user}, {entity: calendar, effect: removes, with: user}, {entity: event, effect: removes, from: Scheduled, with: user}, {entity: task, effect: removes, with: user}, {entity: page, effect: removes, with: user}, {entity: connected-account, effect: removes, from: Connected, with: user}, {entity: attendance, effect: removes, with: user}, {entity: event-reminder, effect: removes, with: user}]
  contexts:
    web: {place: 'web::visitor::confirm-deletion'}
    mobile: {place: 'web::visitor::confirm-deletion'}
---

# Delete the account through the emailed link

## Trigger

A user no longer wants Musubi.

## Outcome

The account, the calendars it owns — for everyone they were shared with — and the events and tasks it created are gone; deletions for items at providers still in use by others are queued.

## Edge cases

- Deleting the account is not handing calendars over: members of a calendar the person owned lose it.
