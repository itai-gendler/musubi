---
entities:
- {entity: connected-account, shows: [Provider, Account name], collects: [Server address]}
- {entity: calendar, shows: [Name, Color]}
references:
- {kind: code, role: implementation, target: apps/client/components/calendar/SyncCalendarModal.tsx}
---

# Sync calendar

Connecting Google, Outlook, iCloud or other CalDAV accounts, the accounts already connected, and opening an invite link.
