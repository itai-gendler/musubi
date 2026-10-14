---
type: web
actors:
- visitor
- user
entryPoints:
- {web: /app}
- {web: /login}
- {web: '/invite/{token}'}
references:
- {kind: code, role: implementation, target: apps/web/src/routes/app.tsx}
- {kind: code, role: implementation, target: apps/web/src/router.tsx}
- {kind: code, role: implementation, target: apps/api/src/handlers/pages.ts}
---

# Musubi web

The desktop web app: the calendar with its pages and views, tasks, search and the
settings window, together with the sign-in page, invitation page and the pages the
server's emails link to. On a narrow screen it points people to the phone app.
