---
domain: tasks
availability:
- {place: 'web::signed-in'}
- {place: 'mobile::signed-in'}
references:
- {kind: code, role: implementation, target: apps/api/src/handlers/tasks.ts#handlerCreateTask}
- {kind: code, role: implementation, target: apps/web/src/calendar/components/TaskList.tsx}
- {kind: code, role: implementation, target: apps/client/components/tasks/TaskEditorModal.tsx}
---

# Create task

An owner or editor of a calendar that keeps tasks creates a task in it, which becomes the task's home. In a synced task list it is saved in Musubi first and delivered after.
