---
appliesTo:
- {type: capability, id: unlink-event}
- {type: capability, id: remove-task-from-calendar}
- {type: capability, id: link-event}
- {type: capability, id: link-task}
references:
- {kind: code, role: implementation, target: apps/client/components/calendar/EventDetailModal.tsx}
- {kind: doc, role: intent, target: packages/docs/src/content/docs/guides/shared-tasks.mdx, title: Shared tasks}
---

# An event or task is never unlinked from its home

Only calendars other than the home are offered for unlinking or removal; leaving the home means deleting the event or task. The home is chosen at creation and linking never moves it.
