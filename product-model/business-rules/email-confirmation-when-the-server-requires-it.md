---
appliesTo:
- {type: capability, id: sign-up}
- {type: capability, id: sign-in}
- {type: capability, id: confirm-email}
references:
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
---

# Accounts confirm their email only where the server requires it

When the operator requires confirmed addresses, an account cannot sign in with its passphrase until its address is confirmed, and every refused sign-in sends a new link. Otherwise addresses are not confirmed.
