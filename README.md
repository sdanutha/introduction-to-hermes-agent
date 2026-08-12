# Day 2 - Hermes Agent Practical Workflow

Day 2 teaches Hermes Agent as a practical always-on agent workflow system.

The lesson starts with simple CLI use, then moves through tools, memory, skills, cron jobs, and safety decisions. The goal is not to cover every Hermes feature. The goal is to help learners build a small, repeatable workflow that they can trust, inspect, and improve.

## Learning Goal

By the end of Day 2, learners should understand:

1. How to verify a working Hermes installation before adding advanced features.
2. How to use Hermes through the CLI or TUI for inspectable tasks.
3. How toolsets control what Hermes can do.
4. How memory helps Hermes remember stable preferences and project context.
5. How skills turn repeatable procedures into reusable workflows.
6. How cron jobs turn one-off tasks into scheduled automation.
7. How to decide when a task needs human approval, sandboxing, or a narrower toolset.

## Core Teaching Rule

Use this rule throughout the day:

```text
Get one clean chat working first.
Then add tools.
Then add memory.
Then add skills.
Then add cron or gateway automation.
```

If the basic chat is not stable, do not add gateway, cron, or more tool access yet.

### Advanced note: `/goal` + `/yolo` safety envelope

Treat `/yolo` as a **temporary escalation** that should only be combined with `/goal` when the goal is already scoped, verifiable, and reversible.

Minimum guardrails before combining them:

- **Scope**: list allowed paths/file types and explicitly forbid everything else.
- **Verification**: include at least one concrete check command (for example, `git diff --name-only`).
- **Stop condition**: define exactly what “done” means so the agent can stop without drifting.
- **Rollback plan**: state how to undo changes (for example, `git restore --staged --worktree -- <path>`).

**Advanced note (more strict):** if you need `/yolo`, also pin a *proof-of-scope* check like `git diff --name-only -- Day-02-Hermes/` and instruct the agent to abort if any path appears outside the allowlist.

## Demo Scenario

Build a small Hermes workflow for a recurring technical research brief.

The workflow should:

- use a specific, verifiable prompt
- remember stable user preferences
- use or create a reusable skill
- schedule the task with cron
- save or deliver output through a safe target
- include a manual test before trusting the schedule

The content examples are intentionally language-neutral. Learners can later adapt the output language, audience, and format to their own needs.

## Folder Structure

```text
day-02/
  README.md
  prompts/
    hermes-practical-workflow-prompts.md
    hermes-advanced-goal-yolo-prompts.md
  materials/
    hermes-workflow-demo-board.md
    hermes-goal-yolo-demo-board.md
  references/
    hermes-command-cheatsheet.md
    hermes-goal-yolo-cheatsheet.md
```

## How to Use This Day

Start with the prompt playbook:

```text
day-02/prompts/hermes-practical-workflow-prompts.md
```

Use the demo board to track progress:

```text
day-02/materials/hermes-workflow-demo-board.md
```

Keep the command cheatsheet nearby:

```text
day-02/references/hermes-command-cheatsheet.md
```

After learners complete the base workflow, use the advanced goal and YOLO track:

```text
day-02/prompts/hermes-advanced-goal-yolo-prompts.md
day-02/materials/hermes-goal-yolo-demo-board.md
day-02/references/hermes-goal-yolo-cheatsheet.md
```

## Main Workflow

The classroom workflow moves from simple to advanced:

```text
Setup check
-> First useful chat
-> Tool inspection
-> Memory
-> Skills
-> Cron
-> Safety review
-> Capstone workflow
```

## Useful Commands

```bash
hermes
hermes --tui
hermes --continue
hermes doctor
hermes model
hermes tools
hermes skills browse
hermes skills search research
hermes cron list
hermes gateway status
/goal status
/goal pause
/goal resume
/goal clear
/yolo
hermes --yolo
```

## What This Demonstrates

Day 2 demonstrates that Hermes is most useful when learners treat it as a workflow system:

- prompts define the immediate task
- tools define available actions
- memory defines durable context
- skills define reusable procedures
- cron defines recurring execution
- `/goal` defines a persistent objective across turns
- `/yolo` changes the approval boundary for command execution
- review gates define trust boundaries

## Day 1 vs Day 2

Day 1 focuses on:

```text
One agent + skills + SDLC workflow
```

Day 2 focuses on:

```text
Hermes as a persistent workflow agent with memory, skills, and automation
```

## Minimum Acceptance Criteria

The Day 2 smoke test passes when:

- Hermes can complete a normal chat.
- Learners can explain which tools are enabled.
- Learners can write one useful memory item.
- Learners can explain when memory should not be used.
- Learners can run or create one simple skill.
- Learners can create, list, and manually run a cron job.
- Learners can identify at least three safety controls.
- The final workflow has a clear manual verification step.

The advanced Day 2 track passes when:

- Learners can write a scoped `/goal` with verification and a stop condition.
- Learners can pause, resume, inspect, and clear a goal.
- Learners can explain what `/yolo` bypasses.
- Learners can identify when `/yolo` is forbidden.
- Learners can describe the safety envelope required before combining `/goal` and `/yolo`.

## References

- https://hermes-agent.nousresearch.com/docs/getting-started/quickstart/
- https://hermes-agent.nousresearch.com/docs/getting-started/installation/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/tools/
- https://hermes-agent.nousresearch.com/docs/reference/toolsets-reference/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/memory/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/skills/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/cron/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/goals/
- https://hermes-agent.nousresearch.com/docs/reference/slash-commands/
- https://hermes-agent.nousresearch.com/docs/user-guide/security/
