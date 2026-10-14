---
availability:
- {place: 'web::visitor'}
- {place: 'mobile::visitor'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/login.tsx}
- {kind: code, role: implementation, target: apps/client/app/(auth)/sign-up.tsx}
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
- {kind: code, role: implementation, target: packages/db/src/queries/pages.ts#ensureDefaultPage}
---

# Sign up

A visitor creates an account with their name, email and a passphrase. Musubi gives every new account a personal calendar it owns and a first page, and asks for the address to be confirmed first when the server requires it.
