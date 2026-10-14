---
entities:
- {entity: calendar, shows: [Name, Color]}
- {entity: event, shows: [Title, Starts, Ends, All day]}
- {entity: user, shows: [Name, Photo]}
entryPoints:
- {mobile: 'musubi://invite/{token}'}
references:
- {kind: code, role: implementation, target: 'apps/client/app/invite/[token].tsx'}
---

# Invitation

The calendar an invite link opens, with accepting or declining it.
