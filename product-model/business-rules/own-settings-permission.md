---
appliesTo:
- {type: entity, id: user, effect: changes, facts: [Name, Photo, Theme, Default view, Week starts on, Time format, Date format, Default reminder, Event change emails, Calendar order, Set up]}
permits:
- self: true
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/settings.ts#handlerPatchSettings}
---

# Only the user changes their own profile and settings

A user's name, photo, display and reminder settings, calendar order and set-up are theirs alone to change.
