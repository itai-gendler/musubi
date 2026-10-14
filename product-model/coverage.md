---
scope: 'Musubi''s API server, web client and phone app: accounts, calendars and sharing, events, tasks, pages, reminders, provider connections and the sync and delivery that keep them in step.'
method: Static reading of the API routes and handlers, query modules, shared types, auth configuration, web routes and components, and phone app screens at the pinned commit; nothing was executed.
covered:
- description: API routes, request handlers and authorization helpers
  paths: [apps/api/src/index.ts, apps/api/src/handlers/, apps/api/src/permissions.ts, apps/api/src/event_permissions.ts, apps/api/src/task_routes.ts, apps/api/src/invite_preview.ts]
- description: Event change emails and their dispatch
  paths: [apps/api/src/event_notifications.ts, apps/api/src/notification_dispatch.ts]
- description: Provider sync engine, scheduling and delivery of saved changes
  paths: [apps/api/src/sync/, apps/api/src/scheduling.ts]
- description: Database schema and query modules
  paths: [packages/db/src/]
- description: Shared request types, permission matrix and reminder rules
  paths: [packages/types/src/, packages/calendar/src/]
- description: Authentication configuration and account emails
  paths: [packages/auth/src/, packages/emails/src/]
- description: Web client routes, calendar workspace, settings, onboarding and offline copy
  paths: [apps/web/src/routes/, apps/web/src/calendar/, apps/web/src/onboarding/, apps/web/src/auth/, apps/web/src/api/, apps/web/src/offline/]
- description: Phone app screens, components, stores and services
  paths: [apps/client/app/, apps/client/components/, apps/client/store/, apps/client/services/, apps/client/hooks/, apps/client/lib/, apps/client/contexts/, apps/client/db/]
- description: 'API request guards: sign-in, rate limits, client version and proxying'
  paths: [apps/api/src/middleware/require_auth.ts, apps/api/src/middleware/rate_limit.ts, apps/api/src/middleware/require_client_version.ts, apps/api/src/middleware/proxy.ts]
- description: Product and contributor documentation
  paths: [README.md, packages/docs/src/content/docs/, .env.example]
exclusions:
- description: Design system, UI primitives, styling and the UI catalogue
  paths: [packages/design-system/, apps/web/src/components/, apps/web/src/design/, apps/ui-catalog/, apps/client/constants/]
- description: Operations, deployment, CI, release and audit records
  paths: [ops/, scripts/, .github/, docs/, docker-compose.yml, docker-compose.api.yml, docker-compose.dokploy.yml, docker-compose.dokploy.dev.yml, patches/]
- description: Metrics and logging
  paths: [apps/api/src/metrics.ts, apps/api/src/product_metrics.ts, apps/api/src/middleware/log_handler.ts, apps/api/src/middleware/error_handler.ts, apps/api/src/middleware/http_error.ts, packages/config/src/logger.ts]
- description: Independent sync reference host and extracted sync packages used as fixtures
  paths: [apps/sync-reference/, packages/sync-runtime/, packages/sync-codec/, packages/provider-google/]
unmapped:
- description: 'Federation between Musubi servers: cross-server invites, member tokens, the gateway and connected servers'
  paths: [apps/api/src/federation_connections.ts, apps/api/src/federation_origin.ts, apps/api/src/federation_peer.ts, apps/api/src/federation_stream.ts, apps/api/src/federation_tokens.ts, apps/api/src/handlers/federation.ts, apps/api/src/handlers/federation_proxy.ts, apps/web/src/calendar/federated-workspace.ts, apps/web/src/calendar/federation-routing.ts, apps/client/services/federation.ts]
- description: Announcements written in the web admin area and shown to users
  paths: [apps/api/src/handlers/announcements.ts, apps/api/src/middleware/require_admin.ts, apps/web/src/routes/app/admin.tsx, apps/web/src/calendar/components/AdminSettings.tsx, apps/web/src/calendar/components/AnnouncementDialog.tsx, apps/client/components/AnnouncementModal.tsx]
- description: 'Provider meeting features gated by server settings: RSVP and organizer edits, provider reminders, Outlook moves and cancellations, provider meeting creation, explicit event time zones and Google free/busy availability'
  paths: [apps/api/src/handlers/availability.ts, apps/api/src/handlers/outlook_moves.ts, apps/web/src/calendar/components/ProviderMeetingCreateDialog.tsx, apps/web/src/calendar/components/ProviderRsvpEditor.tsx, apps/web/src/calendar/components/ProviderOrganizerEditor.tsx, apps/web/src/calendar/components/ProviderReminderEditor.tsx, apps/web/src/calendar/components/OutlookMoveDialog.tsx, apps/web/src/calendar/components/OutlookCancellationDialog.tsx, apps/web/src/calendar/components/AvailabilitySection.tsx, apps/web/src/calendar/components/TimeZonePicker.tsx, apps/client/components/calendar/AvailabilityModal.tsx, apps/client/components/calendar/OutlookMoveSheet.tsx, apps/client/components/calendar/ProviderRsvpEditor.tsx, apps/client/components/calendar/ProviderOrganizerEditor.tsx, apps/client/components/calendar/ProviderReminderEditor.tsx]
- description: Event delivery conflict resolution and discarding provider alarms
  paths: [apps/api/src/handlers/event_delivery.ts, apps/web/src/calendar/components/EventDeliveryDialog.tsx, apps/client/components/calendar/EventDeliveryModal.tsx]
- description: Web push reminders for closed browser tabs and their server dispatcher
  paths: [apps/web/src/push/, apps/api/src/handlers/push.ts, apps/api/src/reminder_dispatch.ts]
- description: Web notification centre
  paths: [apps/web/src/notifications/]
- description: Android and iOS home-screen widgets and their settings
  paths: [apps/client/modules/, apps/client/widgets/, apps/client/components/calendar/CalendarWidgetSettingsModal.tsx]
- description: Diagnostics, debug reports and developer mode
  paths: [apps/web/src/diagnostics/, apps/client/app/debug.tsx, apps/client/services/debugReport.ts, apps/client/services/developerMode.ts]
- description: Profile photo storage backends
  paths: [apps/api/src/media_storage.ts]
- description: Set-up gates of the signed-in shells, whose hand-off from signing up into set-up crosses signing in and so is carried by no Journey
  paths: [apps/client/app/(tabs)/_layout.tsx]
limitations:
- description: 'Per-provider fidelity of the sync adapters: which event and task fields each provider keeps, and how recurring series and their exceptions map'
  paths: [apps/api/src/sync/adapters/]
---

# Coverage
