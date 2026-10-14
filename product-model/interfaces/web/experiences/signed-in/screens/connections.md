---
entities:
- {entity: connected-account, shows: [Provider, Account name], collects: [Server address]}
- {entity: calendar, shows: [Name, Color]}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/ConnectionsPanel.tsx}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/CaldavDialog.tsx}
---

# Connections

The connected accounts and their state, adding a connection, and joining a calendar from a pasted invite link.
