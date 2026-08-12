# 7. Cron

## Description

Cron runs tasks automatically at a set time. It is good for daily reports, reminders, and repeated checks.

## Goal

Create a task that runs automatically.

Cron can run a task once or on a schedule.

## Setup

Cron jobs need a running gateway.

```powershell
hermes gateway start
```

## Try it

### Create a task with a prompt

You can ask Hermes to create a scheduled task:

```text
Every weekday at 9:00 AM, create a short summary of today's important tasks.
Ask me before you send or share anything.
```

Review the schedule before you confirm it.

### Create a task with the CLI

```powershell
hermes cron create "every 1d at 09:00" "Create a short daily task summary" --name daily-summary
```

## Check the result

### Check the task

```powershell
hermes cron list
hermes cron status
```

### Test and manage the task

```powershell
hermes cron run daily-summary
hermes cron pause daily-summary
hermes cron resume daily-summary
hermes cron remove daily-summary
```

## Safety

- Test the task before using a real schedule.
- Do not share private information.
- Use `pause` to stop a task for now.
- Use `remove` to delete a task.

## Finish check

- The learner can create a cron task.
- The learner can list and test the task.
- The learner can pause and remove the task.

## Official guide

- https://hermes-agent.nousresearch.com/docs/user-guide/features/cron/
