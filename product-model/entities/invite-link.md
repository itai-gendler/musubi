---
references:
- {kind: code, role: implementation, target: packages/db/src/queries/invites.ts}
- {kind: code, role: implementation, target: packages/types/src/invite.ts}
---

# Invite link

A link that lets people with a Musubi account join one calendar. The link itself is the invitation: whoever holds it can see a preview of the calendar and join it.

## Information kept

- **Expires** — when the link stops working, or never
- **People limit** — how many people may join through it, or no limit
- **Uses** — how many people have joined through it
