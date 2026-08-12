# Hermes Advanced Goal and YOLO Prompt Playbook

This playbook is the advanced Day 2 track for learners who already understand the base workflow:

```text
chat -> tools -> memory -> skills -> cron -> safety review
```

The advanced focus is narrower:

- `/goal` keeps Hermes working toward one standing objective across turns.
- `/yolo` removes dangerous command approval prompts for the current session.

Together, they are powerful because they move Hermes from "assistant that waits" toward "agent that keeps going." That power should be taught with explicit boundaries.

Primary sources:

- https://hermes-agent.nousresearch.com/docs/user-guide/features/goals/
- https://hermes-agent.nousresearch.com/docs/reference/cli-commands/
- https://hermes-agent.nousresearch.com/docs/reference/slash-commands/
- https://hermes-agent.nousresearch.com/docs/user-guide/security/
- https://hermes-agent.nousresearch.com/docs/user-guide/configuration/

---

## Teaching Rule

Use this rule throughout the advanced track:

```text
Use /goal when the agent needs persistence.
Use /yolo only when the environment is disposable, constrained, and observable.
Never combine them until the learner can explain the blast radius.
```

---

## Prompt 0 - Advanced Readiness Check

Paste this into Hermes before using `/goal` or `/yolo`.

```text
We are starting an advanced Hermes Agent lab about /goal and /yolo.

First, assess whether this session is ready.

Rules:
- Do not modify files.
- Do not change configuration.
- Do not enable /yolo.
- Do not set a /goal yet.
- Use read-only inspection only if needed.

Return:
1. Current workspace
2. Whether this looks disposable or production-like
3. Whether terminal access is available
4. Whether checkpoints, git, sandboxing, or rollback options are visible
5. Recommended safety mode for this lab
6. One thing we should avoid doing in this workspace
```

Gate:

- The learner can classify the environment before increasing autonomy.
- The answer mentions recovery, not just capability.

---

## Prompt 1 - Write a Goal Contract

Paste this before using `/goal`.

```text
Help me turn this task into a safe /goal command.

Task:
Audit this training repository and improve only the documentation for Day 2.

Constraints:
- Do not touch Day 1 files.
- Do not install dependencies.
- Do not run destructive commands.
- Keep edits limited to Markdown files under Day-02-Harness.
- Show the diff before calling the task done.

Return:
1. A one-sentence goal
2. Scope boundaries
3. Verification command
4. Stop condition
5. The exact /goal command I should use
```

Gate:

- The goal includes a clear outcome and stop condition.
- The goal limits files, tools, and verification.

---

## Prompt 2 - Run a Controlled Goal

Paste the generated `/goal` command from Prompt 1.

Example:

```text
/goal Improve only the Day-02-Harness Markdown documentation by adding one concise advanced note, then show git diff and stop when the diff is ready for review.
```

Watch for:

1. Goal accepted.
2. Hermes starts the first turn immediately.
3. Hermes continues automatically if the judge says the goal is not done.
4. Hermes stops when the final response clearly satisfies the goal, the goal is paused, or the turn budget is reached.

Useful control commands:

```text
/goal status
/goal pause
/goal resume
/goal clear
```

Gate:

- The learner can pause and inspect before the loop does too much.
- The learner can explain why the goal stopped.

---

## Prompt 3 - Goal Debugging Drill

Use this after a goal completes or pauses.

```text
Review the /goal run we just performed.

Rules:
- Do not make new edits.
- Do not set a new goal.

Return:
1. Original goal text
2. Whether the final answer really satisfied the goal
3. Evidence used to decide that
4. Any ambiguity in the goal
5. A better version of the goal for next time
6. Whether /goal should be cleared now
```

Gate:

- Learners see that goal quality matters more than the command itself.
- False positives and false negatives are discussed explicitly.

---

## Prompt 4 - YOLO Risk Classifier

Paste this before toggling `/yolo`.

```text
Classify whether /yolo is appropriate for this task.

Task:
Run a documentation formatter or Markdown lint check on this training repository.

Environment facts:
- This is a local training repository.
- The repository may have uncommitted changes.
- We do not want to delete, move, or overwrite unrelated files.

Return:
1. Whether /yolo is appropriate: Yes, No, or Only in a sandbox
2. What approval prompts /yolo would bypass
3. What risks still remain
4. What hard stop rules should apply
5. Safer alternative if /yolo is not appropriate
```

Gate:

- The learner understands that `/yolo` is not a productivity shortcut for unclear tasks.
- The learner can name what approval prompts are being removed.

---

## Prompt 5 - YOLO Toggle Demonstration

Use only in a disposable or sandboxed environment.

```text
Demonstrate /yolo without changing project files.

Rules:
- Use harmless read-only commands only.
- Do not create, edit, delete, move, or install anything.
- Toggle /yolo on, explain what changed, then toggle it off.
- Confirm the final mode is not YOLO.

Return:
1. Commands or slash commands used
2. What changed when /yolo was enabled
3. What did not change
4. Confirmation that /yolo is off at the end
```

Expected slash command sequence:

```text
/yolo
/yolo
```

Gate:

- Learners see `/yolo` as a session state, not a permanent trust decision.
- The final state is safe.

---

## Prompt 6 - Combined Goal + YOLO Scenario Design

Do not run this yet. Use it to design the scenario.

```text
Design a safe lab scenario that combines /goal and /yolo.

Scenario:
Hermes should fix formatting issues in a throwaway copy of a small Markdown folder.

Rules:
- Do not run the scenario yet.
- Assume the lab uses a disposable git worktree or copy.
- Assume no secrets are present.
- Include checkpoints or git diff review.
- Include a rollback plan.

Return:
1. Why /goal helps
2. Why /yolo might help
3. Preconditions before enabling /yolo
4. Exact /goal text
5. When to toggle /yolo on and off
6. Verification steps
7. Rollback steps
8. Go/No-Go recommendation
```

Gate:

- Learners must design the safety envelope before running the autonomous loop.
- The answer separates "possible" from "approved."

---

## Prompt 7 - Combined Goal + YOLO Execution

Use only after Prompt 6 returns a Go recommendation.

```text
Run the approved /goal + /yolo lab.

Hard rules:
- Work only in the disposable lab workspace.
- Do not touch the original repository.
- Do not access secrets.
- Do not use network access.
- Do not install dependencies.
- Toggle /yolo off as soon as the risky command phase is complete.
- Show the final diff and verification result before declaring success.

Return:
1. Safety precheck
2. /goal command used
3. When /yolo was enabled
4. When /yolo was disabled
5. Files changed
6. Verification result
7. Rollback option
8. Final recommendation
```

Gate:

- `/yolo` is time-boxed.
- The final output is reviewable and reversible.

---

## Prompt 8 - Advanced Safety Review

Use this as the final discussion prompt.

```text
Review the advanced /goal and /yolo lab as a safety gate.

Rules:
- Do not make new changes.
- Be specific about evidence.

Return:
1. What /goal made easier
2. What /goal made riskier
3. What /yolo made easier
4. What /yolo made riskier
5. Which safeguards worked
6. Which safeguards were missing
7. Whether this pattern should be allowed for real work
8. Policy recommendation for future training sessions
```

Gate:

- Learners finish with a policy decision, not just a successful command.

---

## Capstone Prompt

Use this only after learners can pause, resume, clear, and critique a goal.

```text
Create an advanced Hermes Agent operating procedure for using /goal and /yolo safely.

The procedure must cover:
1. When to use /goal
2. How to write a good goal
3. How to monitor and pause a goal
4. When /yolo is allowed
5. When /yolo is forbidden
6. How to combine /goal and /yolo in a disposable environment
7. Required verification evidence
8. Rollback or cleanup steps

Rules:
- Keep it practical.
- Include command examples.
- Do not recommend /yolo for production systems or secret-bearing workspaces.
- End with a checklist trainers can use before approving the lab.
```

---

## Trainer Narration

Use this when presenting:

1. "`/goal` changes the stopping behavior of the agent."
2. "`/yolo` changes the approval behavior of the agent."
3. "Combining them changes both persistence and permission pressure."
4. "Advanced autonomy is useful only when the environment is constrained, observable, and recoverable."
