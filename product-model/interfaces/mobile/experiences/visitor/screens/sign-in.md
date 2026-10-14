---
entities:
- {entity: user, collects: [Email, Passphrase]}
references:
- {kind: code, role: implementation, target: apps/client/app/(auth)/sign-in.tsx}
---

# Sign in

Signing in with an email and passphrase, and asking for a passphrase reset.
