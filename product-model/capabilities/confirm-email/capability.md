---
availability:
- {place: 'web::visitor'}
references:
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
- {kind: code, role: implementation, target: apps/api/src/handlers/pages.ts#handlerEmailVerifiedPage}
---

# Confirm email

On a server that requires confirmed addresses, a person opens the link emailed at sign-up or at a refused sign-in. Opening it confirms the address and signs them in.
