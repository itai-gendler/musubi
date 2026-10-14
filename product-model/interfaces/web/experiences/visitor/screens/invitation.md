---
entities:
- {entity: calendar, shows: [Name, Color]}
- {entity: event, shows: [Title, Starts, Ends, All day]}
- {entity: user, shows: [Name, Photo]}
entryPoints:
- {web: '/invite/{token}'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/invite.$token.tsx}
- {kind: code, role: implementation, target: apps/api/src/invite_preview.ts#buildInvitePreview}
---

# Invitation

The calendar an invite link opens, before signing in: its name, who shared it, who is on it and what is on it in the next 30 days.
