---
id: musubi
summary: An open-source, self-hostable calendar for shared events, meetings and tasks, where one event or task can be linked into several people's calendars and synced with Google, Outlook and CalDAV.
category: calendar
tags:
- shared-calendar
- tasks
- calendar-sync
- caldav
- self-hosted
authors:
- {name: FRGTN.dev, url: 'https://frgtn.dev'}
license: MIT
limitations:
- 'An event or task has one home calendar: only that calendar''s owners and editors, or for a synced calendar the person whose account it comes from, change it or delete it everywhere, wherever else it is linked.'
- Calendar roles are fixed to owner, editor and viewer, held per calendar; there are no permissions per event or per task.
- People join a calendar only through an invite link, and they join as viewers.
- Google Calendar, Outlook and CalDAV calendars are kept in step by polling the provider every few minutes; providers do not push changes.
- 'Musubi keeps calendar sharing to itself: sharing a calendar in Musubi never changes who can see it at Google, Microsoft or a CalDAV server.'
languages:
- en
references:
- {kind: doc, role: intent, target: README.md, title: README}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/guides/introduction.mdx, title: Introduction}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/guides/shared-tasks.mdx, title: Shared tasks}
- {kind: doc, role: context, target: packages/docs/src/content/docs/architecture/data-model.mdx, title: Data model}
- {kind: doc, role: context, target: packages/docs/src/content/docs/reference/reminders.mdx, title: Reminders}
---

# Musubi

Musubi is a shared calendar for family, friends and small teams, on the web and as a
phone app. People keep calendars of their own, share them through invite links as
owners, editors or viewers, and add events and tasks to them. An event or task is
not nested inside one calendar: it is linked into as many calendars as it concerns,
edited once and seen by the members of each, while its home calendar decides who
may change it. Pages gather chosen calendars and item types into views of their
own, people answer whether they are coming to an event, and each person decides
when events remind them. Google Calendar, Outlook, iCloud and other CalDAV accounts
can be connected so their calendars sit beside Musubi's, with changes saved in
Musubi first and delivered to the provider after.

## Intent

In the project's own words, Musubi is "an open-source, self-hostable calendar for
shared events, meetings, and tasks" — "Your people. Your events. One knot." Its
"single load-bearing idea" is that "an event is not owned by a calendar. It is
*linked into* one or more calendars": "one dinner, linked into your calendar and
your partner's, edited once, visible in both." The name means "a knot or
connection", and the aim is "one place to connect your schedule with the people
around you, without giving your calendar data to a third party."
