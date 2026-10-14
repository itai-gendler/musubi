---
domain: pages
availability:
- {place: 'web::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/calendar_pages.ts#handlerDeletePage}
- {kind: code, role: implementation, target: packages/db/src/queries/pages.ts#softDeletePage}
---

# Delete page

A user deletes one of their pages; it cannot be restored. Deleting the default page makes the first remaining page the default.
