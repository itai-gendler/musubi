---
entities:
- {entity: user, collects: [Passphrase]}
entryPoints:
- {web: '/reset-password?token={token}'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/pages.ts#handlerResetPasswordPage}
---

# Reset passphrase

The page a password-reset email links to, where the new passphrase is chosen.
