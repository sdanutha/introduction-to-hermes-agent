# 6. Kanban

## Goal

Show how Hermes can manage longer work.

Use this as an advanced topic.

## Simple idea

```text
Research -> Write -> Review -> Done
```

Kanban uses a task board. The gateway dispatcher starts assigned work.

## Start the board

```powershell
hermes kanban init
hermes gateway start
```

## Create a task

```powershell
hermes kanban create "Research Hermes Desktop" --assignee training-researcher
```

## Watch the work

```powershell
hermes kanban watch
hermes kanban list
hermes kanban show <task_id>
```

You can also use Dashboard to check profiles, sessions, and system status.

## Review

```powershell
hermes kanban block <task_id> "Need more information."
hermes kanban unblock <task_id>
hermes kanban archive <task_id>
```

## Finish check

- The board starts.
- A task has an assignee.
- The learner can watch the task.
- The learner can block or archive a practice task.

Official guide:

- https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban/
