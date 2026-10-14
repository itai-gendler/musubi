---
references:
- {kind: code, role: implementation, target: packages/types/src/pages.ts}
- {kind: code, role: implementation, target: packages/db/src/queries/pages.ts}
---

# Page

A user's own view of the calendars: a name and icon, a view, the calendars it shows and which kinds of item. Pages are never shared; two members of one calendar keep their own.

## Information kept

- **Name** — what the page is called
- **Icon** — one of Musubi's page icons
- **View** — day, week, month, several weeks, agenda or tasks
- **Row height** — how much room an hour takes in the day and week grids
- **Weeks shown** — how many weeks the several-weeks view shows
- **Weekend** — whether the week view shows Saturday and Sunday
- **Nearby months** — whether the month view shows days of the months around it
- **Item types** — which of events, tasks and meetings it shows
- **Calendars shown** — every calendar the user can see except those hidden here, so new ones appear on their own, or only the calendars chosen
- **Default** — whether Musubi opens on it; exactly one page is the default
- **Position** — its place in the list of pages
