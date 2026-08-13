# 6. Kanban

## Description

Kanban is a task board for longer work. It is good for work with steps, roles, and review.

## Goal

Show how Hermes can manage longer work.

Use this as an advanced topic.

## Setup

### Simple idea

```text
Research -> Write -> Review -> Done
```

Kanban uses a task board. The gateway dispatcher starts assigned work.

### Initialize

```powershell
hermes kanban init
hermes gateway start
```

## Try it

### Create a task

```powershell
hermes kanban create "Research Hermes Desktop" --assignee researcher-agent
hermes kanban create "Write a short Hermes summary" --assignee writer-agent
hermes kanban create "Review the Hermes summary" --assignee researcher-agent
```

### Watch the work

```powershell
hermes kanban watch
hermes kanban list
hermes kanban show <task_id>
```

You can also use Dashboard to check profiles, sessions, and system status.

## Safety

- Review task results before accepting them.
- Archive practice tasks after the workshop.

## Finish check

- The board starts.
- A task has an assignee.
- The learner can watch the task.
- The learner can block or archive a practice task.

## Official guide

- https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban/
