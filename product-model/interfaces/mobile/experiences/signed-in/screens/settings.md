---
entities:
- {entity: user, shows: [Name, Email, Photo, Theme, Tab labels, Default view, Week starts on, Time format, Date format, Default reminder, Event change emails], collects: [Name, Email, Photo, Theme, Tab labels, Default view, Week starts on, Time format, Date format, Default reminder, Event change emails]}
references:
- {kind: code, role: implementation, target: apps/client/app/(tabs)/settings.tsx}
---

# Settings

Appearance, date and time formats, reminders, email notifications, delivery status and the account.
