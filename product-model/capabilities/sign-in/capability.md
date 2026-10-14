---
availability:
- {place: 'web::visitor'}
- {place: 'mobile::visitor'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/login.tsx}
- {kind: code, role: implementation, target: apps/client/app/(auth)/sign-in.tsx}
- {kind: code, role: implementation, target: apps/client/components/auth/SocialAuthButtons.tsx}
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
---

# Sign in

A visitor signs in with their email and passphrase, or with a Google, Microsoft or Apple account where the server is set up for it.
