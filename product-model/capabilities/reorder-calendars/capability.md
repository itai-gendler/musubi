---
domain: calendars
availability:
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/client/app/(tabs)/calendars.tsx}
- {kind: code, role: implementation, target: apps/client/components/calendar/ReorderableCalendarList.tsx}
---

# Reorder calendars

A phone user drags their calendars into the order they want. The order follows the account, and decides whose reminder rule an event linked into several calendars follows.
