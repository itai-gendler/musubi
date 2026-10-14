---
domain: connections
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/ConnectionsPanel.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/SyncCalendarModal.tsx}
- {kind: code, role: implementation, target: apps/api/src/handlers/caldav.ts#handlerConnectCaldav}
- {kind: code, role: implementation, target: apps/api/src/sync/engine.ts#syncUser}
---

# Connect calendar account

A user connects a Google, Outlook, iCloud or other CalDAV account. Musubi brings in each of its calendars as a synced calendar the user is a member of — owner where the provider lets them write, viewer where it is read-only — with their events, and task lists where the connection includes tasks.
