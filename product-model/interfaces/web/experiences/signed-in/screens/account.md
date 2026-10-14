---
entities:
- {entity: user, shows: [Name, Email, Photo], collects: [Name, Email, Photo]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/AccountPanel.tsx}
---

# Account

The user's profile and security: photo, display name, email, resetting the passphrase and deleting the account.
