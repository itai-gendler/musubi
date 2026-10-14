---
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/settings.ts#handlerPatchSettings}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/settings/GeneralPanel.tsx}
- {kind: code, role: implementation, target: apps/client/app/(tabs)/settings.tsx}
---

# Change general settings

A user sets how Musubi looks and behaves for them: theme, opening view, week start, time and date formats, their default reminders and whether they are emailed about changes to events they attend. Settings follow the account to every device.
