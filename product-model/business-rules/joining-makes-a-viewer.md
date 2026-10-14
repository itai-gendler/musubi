---
appliesTo:
- {type: capability, id: join-calendar}
- {type: capability, id: create-invite-link}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/calendars.ts#joinCalendarFromInvite}
- {kind: code, role: implementation, target: apps/api/src/handlers/calendars.ts#handlerJoinCalendar}
---

# Joining through an invite link makes the person a viewer

Whoever joins a calendar through an invite link joins as a viewer; the owner makes them an editor afterwards. A calendar is joined only through a live invite link, never by its identifier alone.
