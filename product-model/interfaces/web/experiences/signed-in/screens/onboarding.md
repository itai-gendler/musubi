---
entities:
- {entity: user, collects: [Name]}
- {entity: calendar, collects: [Name, Color]}
references:
- {kind: code, role: implementation, target: apps/web/src/onboarding/Onboarding.tsx#Onboarding}
---

# Welcome

The first-run set-up in three steps: the user's name, their personal calendar, and connecting another calendar provider.
