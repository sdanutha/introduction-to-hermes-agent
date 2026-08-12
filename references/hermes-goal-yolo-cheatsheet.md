# Hermes Goal and YOLO Cheatsheet

This cheatsheet is for the advanced Day 2 track.

Primary docs:

- https://hermes-agent.nousresearch.com/docs/user-guide/features/goals/
- https://hermes-agent.nousresearch.com/docs/reference/cli-commands/
- https://hermes-agent.nousresearch.com/docs/reference/slash-commands/
- https://hermes-agent.nousresearch.com/docs/user-guide/security/
- https://hermes-agent.nousresearch.com/docs/user-guide/configuration/

## Mental Model

```text
/goal changes persistence.
/yolo changes approval behavior.
Together they increase autonomy and blast radius.
```

Use `/goal` when Hermes should keep working across turns until a stated objective is satisfied, paused, cleared, blocked, or the turn budget is reached.

Use `/yolo` only when bypassing approval prompts is acceptable because the workspace is disposable, constrained, observable, and recoverable.

## Goal Commands

Inside chat:

```text
/goal <objective>
/goal
/goal status
/goal pause
/goal resume
/goal clear
```

Meaning:

| Command | Use |
| --- | --- |
| `/goal <objective>` | Set or replace the standing goal and start immediately |
| `/goal` | Show current goal status |
| `/goal status` | Show current goal status |
| `/goal pause` | Stop automatic continuation without clearing the goal |
| `/goal resume` | Resume the goal loop |
| `/goal clear` | Remove the standing goal |

## Good Goal Shape

Use this structure:

```text
/goal <outcome>, limited to <scope>, using <allowed tools>, avoiding <forbidden actions>, verified by <evidence>, and stop after showing <final review artifact>.
```

Examples:

```text
/goal Inspect Day-02-Harness Markdown files, identify documentation gaps about /goal and /yolo, do not edit files, and stop after returning a concise improvement plan.
```

```text
/goal Improve only Markdown files under Day-02-Harness for the advanced /goal and /yolo lesson, avoid Day-01-SDLC, do not install dependencies, verify with git diff, and stop when the diff is ready for review.
```

Avoid:

```text
/goal Make this better.
```

```text
/goal Fix everything and keep going until it is perfect.
```

## Goal Watchpoints

Watch for:

- vague completion criteria
- goals that include unrelated tasks
- goals that require secrets or production access
- goals that can trigger external side effects
- goals that cannot be verified
- repeated continuation with no new evidence

Pause when:

```text
/goal pause
```

Clear when the goal is done or unsafe to continue:

```text
/goal clear
```

## YOLO Commands

Start a session with YOLO:

```bash
hermes --yolo
hermes chat --yolo
```

Toggle during a session:

```text
/yolo
```

Environment variable:

```bash
HERMES_YOLO_MODE=1 hermes
```

Configuration equivalent:

```yaml
approvals:
  mode: off
```

Safer approval configuration for many real workflows:

```yaml
approvals:
  mode: manual
```

or:

```yaml
approvals:
  mode: smart
```

## What YOLO Does

YOLO bypasses dangerous command approval prompts for the current session.

It does not mean:

- the task is safe
- the agent is correct
- the workspace is disposable
- secrets are protected
- external systems cannot be affected
- review is no longer needed

Hermes still has a hardline blocklist for catastrophic commands that should not run even when YOLO or approvals-off mode is active.

## When YOLO Is Reasonable

Use only when all are true:

- the workspace is disposable or sandboxed
- no secrets are reachable
- commands are scoped to a known folder
- rollback is available
- the task is repetitive and low judgment
- the expected commands are understood
- output is reviewed before being trusted

Good examples:

```text
Run a formatter in a throwaway worktree and show the diff.
```

```text
Run a read-only inspection loop in a disposable container.
```

## When YOLO Is Forbidden

Do not use YOLO for:

- production systems
- secret-bearing repositories
- broad filesystem cleanup
- database migrations
- cloud infrastructure changes
- credential or config edits
- external messaging or email delivery
- tasks with unclear scope
- tasks where rollback is unknown

## Goal + YOLO Pattern

Safe sequence:

```text
1. Write the goal contract.
2. Verify the workspace is disposable.
3. Confirm rollback.
4. Set the goal.
5. Toggle /yolo only for the narrow command phase.
6. Toggle /yolo off immediately.
7. Show diff or output.
8. Verify.
9. Clear the goal.
```

Example:

```text
/goal In the disposable markdown-lab copy only, format Markdown files, avoid network access and installs, show git diff, and stop when the formatted diff is ready for review.
```

Then, only if the environment is approved:

```text
/yolo
```

After the narrow command phase:

```text
/yolo
/goal status
/goal clear
```

## Trainer Safety Checklist

Before approving `/goal`:

1. Is the goal specific?
2. Is the scope narrow?
3. Is verification defined?
4. Is there a stop condition?
5. Can the learner pause or clear it?

Before approving `/yolo`:

1. Is the environment disposable?
2. Are secrets absent?
3. Are external side effects impossible or blocked?
4. Is rollback available?
5. Is YOLO necessary, not merely convenient?

Before approving `/goal` + `/yolo`:

1. Has the combined blast radius been explained?
2. Is YOLO time-boxed?
3. Is the final artifact reviewable?
4. Is the cleanup command known?
5. Is there an explicit Go/No-Go decision?
