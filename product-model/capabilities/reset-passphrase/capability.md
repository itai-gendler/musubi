---
domain: account
availability:
- {place: 'web::visitor'}
- {place: 'mobile::visitor'}
- {place: 'web::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/login.tsx}
- {kind: code, role: implementation, target: apps/client/app/(auth)/sign-in.tsx}
- {kind: code, role: implementation, target: apps/api/src/handlers/pages.ts#handlerResetPasswordPage}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/AccountPanel.tsx}
---

# Reset passphrase

A person asks for a link to choose a new passphrase, from the sign-in page or from their account, and chooses it on the page the emailed link opens. The request is answered the same way whether or not the address has an account.
