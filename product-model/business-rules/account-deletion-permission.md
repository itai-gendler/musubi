---
appliesTo:
- {type: entity, id: user, effect: removes}
permits:
- actors:
  - visitor
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/users.ts#handlerConfirmDeleteUser}
---

# An account is deleted only from the link emailed to it

Asking to delete an account only sends a confirmation link to its address; the account is deleted by whoever opens that link, valid for an hour and usable once, and confirms. No session is needed on the page the link opens: the link is the proof.
