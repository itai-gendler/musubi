---
appliesTo:
- {type: capability, id: email-invitation}
- {type: capability, id: reset-passphrase}
- {type: capability, id: email-event-changes}
- {type: capability, id: delete-account}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/invites.ts#handlerSendCalendarInvite}
---

# Musubi's emails need the server's mail to be configured

Invitations, passphrase resets, account deletion and event change emails go out only from a server with mail configured. Without it, an email invitation is refused and the person copies the link instead.
