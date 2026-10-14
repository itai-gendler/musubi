---
appliesTo:
- {type: capability, id: create-event}
- {type: capability, id: create-task}
- {type: capability, id: deliver-changes-to-providers}
- {type: capability, id: retry-delivery}
references:
- {kind: doc, role: intent, target: packages/docs/src/content/docs/guides/shared-tasks.mdx, title: Shared tasks}
---

# Event and task changes are saved in Musubi before they reach a provider

A change to an event or task in a synced calendar is saved in Musubi together with its deliveries; a successful save says nothing about whether every provider has taken it yet.
