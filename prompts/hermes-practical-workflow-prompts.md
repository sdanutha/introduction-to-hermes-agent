# Hermes Practical Workflow Prompt Playbook

This playbook is the Day 2 companion to the Day 1 SDLC skills demo.

Day 2 focuses on Hermes as a persistent workflow agent:

- CLI or TUI first
- tools second
- memory third
- skills fourth
- cron only after the base workflow is stable

Important:

```text
Do not start with gateway, cron, or broad tool access.
Start with one clean, inspectable Hermes session.
```

---

## Before Class

Learners should have Hermes installed and configured.

Recommended starting checks:

```bash
hermes doctor
hermes model
hermes
```

Windows users should run Hermes inside WSL2.

Hermes requires a model with at least 64K context.

---

## Prompt 0 - Setup Sanity Check

Paste this into Hermes.

```text
We are running a Day 2 Hermes Agent practical workflow demo.

First, help me verify the setup.

Rules:
- Do not change files.
- Do not change configuration.
- Do not install anything.
- If you need a command, explain what it checks before running it.

Return:
1. Current working directory
2. Active model or provider if visible
3. Available tool categories if visible
4. Any setup risk or missing prerequisite
5. One recommended next step
```

Gate:

- Hermes responds normally.
- No configuration is changed.
- The learner knows whether the base setup is usable.

---

## Prompt 1 - First Useful Chat

Paste this into Hermes from a project directory.

```text
Inspect this workspace and summarize what it appears to contain.

Rules:
- Do not modify files.
- Prefer a concise summary.
- Mention which files or folders you inspected.

Return:
1. Project purpose
2. Main folders
3. Likely entrypoints
4. Useful commands to try next
5. Any uncertainty you have
```

Gate:

- The answer is grounded in real files.
- The answer includes uncertainty instead of guessing.

---

## Prompt 2 - Tool Awareness

Paste this into Hermes.

```text
Explain what tools you currently have available in this session.

For each available tool category, tell me:
1. What it can do
2. A safe example task
3. A risky example task
4. Whether human approval should be required

Do not run commands yet.
```

Gate:

- Learners can name the tool categories.
- Learners can explain why tool access should be limited.

---

## Prompt 3 - Safe Terminal Lab

Paste this into Hermes.

```text
Use the terminal only for read-only inspection.

Task:
- Show the current directory.
- Show the top-level files and folders.
- Identify the package manager or runtime if one is obvious.

Rules:
- Do not edit files.
- Do not install dependencies.
- Do not delete, move, or rename anything.
- Explain each command before running it.

Return:
1. Commands run
2. What each command showed
3. What you would check next
```

Gate:

- Only read-only commands are used.
- The learner sees the relationship between prompt constraints and tool behavior.

---

## Prompt 4 - Memory: Add Stable Preferences

Paste this into Hermes.

```text
Remember these stable preferences for future sessions:

- I prefer concise answers with practical examples.
- When working on code, include verification commands.
- When a task is risky, ask for approval before making destructive changes.

After saving this, tell me:
1. Which items are good memory candidates
2. Which items should not be stored as memory
3. How I can verify this memory later
```

Gate:

- Memory stores stable preferences, not temporary task details.
- No secrets are saved.

---

## Prompt 5 - Memory: Project Context

Paste this into Hermes from the training repo.

```text
Remember this project context:

- This workspace is used for agent workflow training.
- Day 1 covers a single-agent SDLC workflow.
- Day 2 covers Hermes memory, skills, tools, cron, and safety.

Keep the memory short and reusable.

Return:
1. The memory you saved or propose to save
2. Why it is useful across sessions
3. What you intentionally did not save
```

Gate:

- Project memory is short.
- It avoids noisy classroom transcript details.

---

## Prompt 6 - Explore Skills

Paste this into Hermes.

```text
Help me understand the installed skills.

Rules:
- Do not install new skills yet.
- Do not modify existing skills.

Return:
1. A short explanation of what a skill is
2. How skills are triggered
3. A few installed skills that look useful for technical work
4. One example task for each selected skill
5. When not to use a skill
```

Gate:

- Learners understand skills as reusable procedures.
- No new skill is installed yet.

---

## Prompt 7 - Create a Small Skill

Paste this into Hermes.

```text
Create a simple skill named `research-brief`.

Purpose:
Summarize technical sources into a concise, decision-oriented brief.

The skill should produce:
1. Context
2. Key findings
3. Practical implications
4. Risks or limitations
5. Recommended next actions
6. Source links or evidence used

Rules:
- Keep the skill generic and reusable.
- Do not include language-specific requirements.
- Do not include secrets, personal data, or local machine details.
- Keep the skill short enough for classroom review.

After creating it, report:
1. File path
2. Skill trigger name
3. What the skill does
4. How to test it
```

Gate:

- The skill exists.
- The skill is generic.
- The skill can be reviewed by the class.

---

## Prompt 8 - Use the Skill

Paste this into Hermes after the skill exists.

```text
Use the `research-brief` skill.

Topic:
Compare two approaches for using an AI agent in a software team:
- interactive assistant
- scheduled automation

Rules:
- Keep it concise.
- Include practical implications.
- Mention risks and recommended next actions.
- Use web research only if available and appropriate.

Return the brief in the skill's format.
```

Gate:

- The response follows the skill structure.
- The learner can explain how the skill changed the output.

---

## Prompt 9 - One-Shot Cron Job

Paste this into Hermes.

```text
Create a one-shot reminder for 30 minutes from now:

Task:
Review the Day 2 Hermes workflow notes and write down one improvement for the next class.

Delivery:
Use the safest local or origin delivery option available.

Rules:
- Do not connect a new messaging platform.
- Do not use broad tool access.
- After creating it, show me how to list, run, pause, resume, and remove the job.
```

Gate:

- Learners can list the job.
- Learners know how to remove it.

---

## Prompt 10 - Recurring Cron Job

Paste this into Hermes.

```text
Create a recurring scheduled task:

Schedule:
Every weekday at 9:00 AM.

Task:
Create a short technical research brief about recent AI agent tooling updates.

Use:
- the `research-brief` skill if available
- local delivery unless another safe delivery target is already configured

Rules:
- Do not connect a new messaging platform.
- Do not include secrets.
- Do not send duplicate messages.
- Do not create additional cron jobs from inside the job.

After creating it:
1. Show the job name or ID.
2. Show how to manually run it once.
3. Show how to pause it.
4. Show how to remove it after the demo.
```

Gate:

- Learners understand schedule, delivery, and manual testing.
- The job can be paused or removed.

---

## Prompt 11 - Safety Review

Paste this into Hermes.

```text
Review the workflow we just built.

Workflow:
- Hermes CLI session
- memory preferences
- `research-brief` skill
- scheduled research brief cron job

Rules:
- Do not change anything.
- Review it as a safety gate.

Return:
1. What is safe enough for a classroom demo
2. What would need more control in production
3. Which tools should stay disabled unless needed
4. What human approval checkpoints are required
5. Final recommendation: Go, Go with comments, or No-Go
```

Gate:

- The workflow ends with a decision.
- Learners see automation as a trust boundary, not just a convenience.

---

## Capstone Prompt

Use this after learners understand the step-by-step version.

```text
Build a small Hermes workflow for a recurring technical research brief.

Goal:
Every weekday morning, produce a concise research brief about recent AI agent tooling updates.

Workflow requirements:
1. Verify Hermes setup first.
2. Confirm the available tools.
3. Save only stable memory preferences.
4. Create or use a `research-brief` skill.
5. Create a scheduled cron job.
6. Use local or origin delivery unless a safe messaging target is already configured.
7. Manually run the job once for verification.
8. End with a safety review and Go/No-Go decision.

Rules:
- Do not include language-specific output requirements.
- Do not store secrets in memory or skills.
- Do not connect new messaging platforms unless I explicitly approve.
- Do not enable broad tools unless the task needs them.
- Ask before making destructive changes.

Return:
1. Setup status
2. Memory saved
3. Skill created or used
4. Cron job created
5. Manual test result
6. Safety review
7. Final recommendation
```

---

## Trainer Narration

Use this when presenting:

1. "Day 1 taught the agent to follow an engineering process."
2. "Day 2 teaches Hermes as a persistent workflow agent."
3. "The important sequence is chat, tools, memory, skills, automation."
4. "Automation is useful only when the task is inspectable, recoverable, and safe."
