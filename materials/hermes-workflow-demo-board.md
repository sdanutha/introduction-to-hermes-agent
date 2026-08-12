# Hermes Workflow Demo Board

## Goal

Build a small, safe Hermes workflow that turns a repeatable technical research task into a scheduled automation.

## Demo Workflow

```text
Verify setup
-> inspect tools
-> save stable memory
-> create or use a skill
-> schedule a cron job
-> run it manually
-> safety review
```

## Current State

- Hermes should already be installed.
- A model provider should already be configured.
- Learners should be able to start `hermes` or `hermes --tui`.
- Gateway and external delivery are optional.
- Cron should not be trusted until a manual run succeeds.

## Acceptance Criteria

- Hermes completes a normal chat.
- The learner can explain the enabled tool categories.
- At least one useful memory item is saved or proposed.
- A reusable `research-brief` skill exists or is used.
- A cron job is created with a clear schedule and delivery target.
- The cron job is manually run once.
- The workflow ends with a Go/No-Go safety decision.

## Level Progression

| Level | Activity | What learners should notice |
| --- | --- | --- |
| 1 | First chat | Hermes must work before anything else matters |
| 2 | Tool inspection | Capabilities should match the task |
| 3 | Read-only terminal | Good prompts create safe boundaries |
| 4 | Memory | Store durable context, not noisy details |
| 5 | Skills | Reusable procedures improve consistency |
| 6 | Cron | Automation needs delivery, testing, and cleanup |
| 7 | Safety review | Trust requires evidence and rollback paths |

## Handoff Template

```text
Goal:
Current state:
Tools used:
Memory saved:
Skill used or created:
Cron job:
Manual verification:
Known risks:
Next decision:
```

## Demo Checklist

- [ ] `hermes doctor` result reviewed.
- [ ] Basic Hermes chat works.
- [ ] Tools are inspected before use.
- [ ] Read-only terminal lab completed.
- [ ] Stable memory item added or proposed.
- [ ] Project context memory added or proposed.
- [ ] Skills explained.
- [ ] `research-brief` skill created or used.
- [ ] One-shot reminder created and listed.
- [ ] Recurring research brief cron job created.
- [ ] Cron job manually run once.
- [ ] Cron job pause/remove commands are known.
- [ ] Safety review completed.
- [ ] Final Go/No-Go decision made.

## Safety Notes

Use these questions during discussion:

1. Does the workflow need file write access?
2. Does the workflow need terminal access?
3. Does the workflow need web access?
4. Does the workflow need external message delivery?
5. Could this job leak secrets?
6. Could this job spam a channel?
7. How do we pause or remove it?
8. What evidence proves it worked?

## Good Memory Examples

```text
I prefer concise answers with practical examples.
```

```text
When working on code, include verification commands.
```

```text
This workspace is used for agent workflow training.
```

## Poor Memory Examples

```text
Remember this temporary error from today's demo.
```

```text
Remember my API key is ...
```

```text
Remember every command output from this session.
```

## Final Review Questions

Ask learners:

1. What did Hermes remember?
2. What procedure became a skill?
3. What task became scheduled?
4. What tools were actually necessary?
5. What should still require human approval?
