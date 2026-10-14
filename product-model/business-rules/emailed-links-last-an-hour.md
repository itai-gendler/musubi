---
appliesTo:
- {type: capability, id: reset-passphrase}
- {type: capability, id: confirm-email}
- {type: capability, id: change-email}
- {type: capability, id: delete-account}
references:
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
---

# Links Musubi emails about an account last one hour

Passphrase reset, email confirmation, email change and account deletion links work for one hour.
