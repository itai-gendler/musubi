---
entities:
- {entity: calendar, shows: [Name, Color]}
- {entity: event, shows: [Title, Starts, Ends, All day]}
- {entity: user, shows: [Name, Photo]}
entryPoints:
- {web: '/invite/{token}'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/invite.$token.tsx}
---

# Invitation

The calendar an invite link opens, for a signed-in user, with joining it.
