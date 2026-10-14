---
appliesTo:
- {type: entity, id: user, effect: changes, facts: [Email, Email confirmed, Passphrase]}
permits:
- actors:
  - visitor
references:
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
---

# An account's email and passphrase change only through links emailed to it

A new passphrase, a confirmed address and a move to another address take effect only from the link Musubi emailed to the account, opened on the page it leads to.
