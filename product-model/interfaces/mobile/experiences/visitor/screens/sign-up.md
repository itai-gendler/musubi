---
entities:
- {entity: user, collects: [Name, Email, Passphrase]}
references:
- {kind: code, role: implementation, target: apps/client/app/(auth)/sign-up.tsx}
---

# Create account

Creating an account with a name, email and passphrase.
