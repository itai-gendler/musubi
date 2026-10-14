---
appliesTo:
- {type: capability, id: sign-up}
- {type: capability, id: reset-passphrase}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/login.tsx}
---

# A passphrase has at least 8 characters

Signing up and resetting a passphrase refuse one shorter than 8 characters.
