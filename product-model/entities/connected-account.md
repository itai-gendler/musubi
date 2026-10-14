---
relations:
- {entity: calendar, verb: mirrors, cardinality: one-to-many}
- {entity: delivery, verb: carries, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: packages/db/src/schema.ts}
- {kind: code, role: implementation, target: apps/api/src/handlers/connections.ts}
---

# Connected account

A Google, Microsoft, iCloud or other CalDAV account a user connected, whose calendars Musubi keeps beside its own. A user may connect several accounts of one provider.

## Information kept

- **Provider** — Google, Outlook, iCloud or another CalDAV server
- **Account name** — the provider account's own label
- **Server address** — for a CalDAV account, the server it reaches
- **Includes tasks** — whether the account's task lists were connected as well as its calendars

## States

### Connected

Musubi reads and writes its calendars.

### Needs reconnecting

The provider stopped accepting Musubi's access; its calendars show that they need attention until the user connects the account again.
