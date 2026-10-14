---
domain: pages
availability:
- {place: 'web::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendar_pages.ts#handlerCreatePage}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/PageSettingsDialog.tsx}
---

# Create page

A user adds a page of their own, with a name, icon and view; it starts out showing every calendar they can see.
