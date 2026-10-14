---
entities:
- {entity: user, collects: [Name, Email, Passphrase]}
entryPoints:
- {web: /login}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/login.tsx}
---

# Sign in

Signing in, or creating an account, with an email and passphrase or a Google, Microsoft or Apple account the server offers; also where a forgotten passphrase is asked for.
