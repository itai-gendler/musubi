---
domain: sharing
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerCreateCalendarInvite}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/ShareCalendarDialog.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/InvitesModal.tsx}
---

# Create invite link

An owner or editor creates a link that lets people join the calendar, optionally expiring after some days or limited to a number of people.
