---
domain: account
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/users.ts#handlerUploadAvatar}
---

# Change profile photo

A user sets the photo shown beside their name to people they share calendars with.
