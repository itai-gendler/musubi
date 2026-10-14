---
appliesTo:
- {type: capability, id: set-default-page}
- {type: capability, id: delete-page}
- {type: capability, id: create-page}
references:
- {kind: code, role: implementation, target: packages/db/src/queries/pages.ts#softDeletePage}
- {kind: code, role: implementation, target: packages/db/src/queries/pages.ts#reorderPages}
---

# A user has exactly one default page

Musubi opens on the default page. Setting another as default takes the mark from the previous one, and deleting the default passes it to the first remaining page; the last page cannot be deleted.
