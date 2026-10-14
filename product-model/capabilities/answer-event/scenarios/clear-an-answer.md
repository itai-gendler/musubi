---
kind: alternative
routes:
  web: Web
  mobile: Mobile
steps:
- text: The User chooses Clear answer
  kind: actor
  actor: user
  entities: [{entity: attendance, effect: reads, facts: [Answer]}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
- text: The Product removes the answer
  kind: product
  actor: user
  entities: [{entity: attendance, effect: removes}]
  contexts:
    web: {place: 'web::signed-in::event'}
    mobile: {place: 'mobile::signed-in::event'}
---

# Clear an answer

## Trigger

A user no longer wants to give an answer.

## Outcome

The user is off the attendee list.
