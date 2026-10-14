---
kind: person
acts: external
relations:
- {entity: calendar-membership, verb: holds, cardinality: one-to-many}
- {entity: calendar, verb: owns, cardinality: one-to-many}
- {entity: event, verb: organizes, cardinality: one-to-many}
- {entity: task, verb: creates, cardinality: one-to-many}
- {entity: page, verb: keeps, cardinality: one-to-many}
- {entity: connected-account, verb: connects, cardinality: one-to-many}
- {entity: attendance, verb: gives, cardinality: one-to-many}
- {entity: event-reminder, verb: sets, cardinality: one-to-many}
- {entity: change-notice, verb: receives, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: packages/db/src/schema.ts}
- {kind: code, role: implementation, target: packages/types/src/settings.ts#SettingsSchema}
- {kind: code, role: implementation, target: packages/auth/src/lib/auth.ts}
---

# User

A person signed in to a Musubi server with their own account. In every calendar they belong to they hold a membership that makes them its owner, an editor or a viewer.

## Information kept

- **Name** — the display name people they share calendars with see
- **Email** — the address they sign in with and receive Musubi's emails at
- **Email confirmed** — whether they opened the confirmation link sent to that address
- **Passphrase** — the secret of at least 8 characters they sign in with, unless they sign in with a Google, Microsoft or Apple account
- **Photo** — an optional JPEG, PNG or WebP picture of up to 256 KB shown beside their name
- **Theme** — system, dark or light
- **Default view** — the view the phone app opens on: day, week, month or schedule
- **Week starts on** — Monday or Sunday
- **Time format** — 12-hour or 24-hour
- **Date format** — day-month-year, month-day-year or year-month-day
- **Tab labels** — whether the phone app's tab bar shows labels
- **Default reminder** — when events remind them unless a calendar or an event says otherwise: minutes before a timed event, and a time on a day before an all-day event; 10 minutes before and 18:00 the day before at first
- **Event change emails** — whether they are emailed when an event they attend moves or is cancelled; on at first
- **Calendar order** — the order of their calendars, which also decides whose reminder rule an event linked into several of them follows
- **Time zone** — the zone their all-day reminders are worked out in
- **Set up** — whether they finished the first-run set-up
