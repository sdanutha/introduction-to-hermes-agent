# Hermes Command Cheatsheet

This cheatsheet is for Day 2 classroom use.

Primary docs:

- https://hermes-agent.nousresearch.com/docs/getting-started/quickstart/
- https://hermes-agent.nousresearch.com/docs/getting-started/installation/
- https://hermes-agent.nousresearch.com/docs/reference/cli-commands/
- https://hermes-agent.nousresearch.com/docs/reference/toolsets-reference/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/skills/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/cron/
- https://hermes-agent.nousresearch.com/docs/user-guide/security/

## Install

Linux, macOS, WSL2:

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
source ~/.bashrc
```

Windows:

```text
Use WSL2, then run the Linux install command inside WSL2.
```

## First Setup

```bash
hermes setup
hermes model
hermes doctor
hermes
hermes --tui
```

Notes:

- `hermes setup` runs the broader setup wizard.
- `hermes model` configures provider and model.
- `hermes doctor` checks common setup issues.
- Hermes requires a model with at least 64K context.

## Sessions

```bash
hermes
hermes --tui
hermes --continue
hermes -c
hermes sessions list
```

## Tools

```bash
hermes tools
hermes chat --toolsets web,file,terminal
hermes chat --toolsets debugging
hermes chat --toolsets all
```

Toolset idea:

```text
Enable only the capabilities needed for the task.
```

Common tool categories:

| Tool category | Typical use | Risk |
| --- | --- | --- |
| file | read and edit files | accidental overwrite |
| terminal | run commands | destructive commands or secret leakage |
| web | search and extract pages | unreliable sources or prompt injection |
| browser | inspect websites | external state changes |
| memory | remember stable context | storing secrets or stale assumptions |
| skills | reusable procedures | outdated or over-broad instructions |
| cronjob | scheduled automation | spam, stale jobs, unattended actions |

## Terminal Backend

```bash
hermes config set terminal.backend docker
hermes config set terminal.backend ssh
```

Use sandboxing for demos and production-like automation when possible.

## Skills

```bash
hermes skills browse
hermes skills browse --source official
hermes skills search research
hermes skills inspect openai/skills/k8s
hermes skills install openai/skills/k8s
```

Inside chat:

```text
/plan Design a REST API for a todo app.
/skills browse
/skills search research
```

Skill principles:

- Use skills for repeatable procedures.
- Keep skills short and task-specific.
- Do not store secrets in skills.
- Review generated skills before relying on them.

## Cron

Inside chat:

```text
/cron add 30m "Review the demo notes"
/cron add "every 2h" "Check the project status"
/cron add "every 1h" "Summarize new feed items" --skill research-brief
/cron list
/cron pause <job_id>
/cron resume <job_id>
/cron run <job_id>
/cron remove <job_id>
```

Standalone CLI:

```bash
hermes cron create "every 2h" "Check project status"
hermes cron create "every 1d at 09:00" "Create a short technical research brief"
hermes cron create "every 1d at 09:00" "Create a short technical research brief" --skill research-brief
hermes cron list
hermes cron run <job_id>
hermes cron pause <job_id>
hermes cron resume <job_id>
hermes cron remove <job_id>
hermes cron status
```

Run inside a project directory:

```bash
hermes cron create "every 1d at 09:00" \
  "Audit this repo and summarize open risks" \
  --workdir /path/to/project
```

Cron notes:

- Cron execution is handled by the gateway daemon.
- Local CLI delivery saves output locally by default.
- Cron jobs run in fresh agent sessions.
- Cron jobs should not recursively create more cron jobs.
- Manual run once before trusting a recurring schedule.

## Gateway

```bash
hermes gateway setup
hermes gateway
hermes gateway status
hermes gateway install
```

Gateway rule:

```text
Only add gateway after the CLI workflow is stable.
```

## Troubleshooting

Recommended recovery order:

```bash
hermes doctor
hermes model
hermes setup
hermes sessions list
hermes --continue
hermes gateway status
```

Common symptoms:

| Symptom | Likely cause | First check |
| --- | --- | --- |
| `hermes` not found | shell path not refreshed | `source ~/.bashrc` |
| API key error | provider not configured | `hermes model` |
| broken or empty replies | wrong model/provider | `hermes model` |
| old session missing | profile/session mismatch | `hermes sessions list` |
| gateway receives nothing | token or allowlist issue | `hermes gateway status` |
| cron does not run | gateway not ticking or job paused | `hermes cron status` |

## Safety Checklist

Before enabling automation, ask:

1. What tools does the task actually need?
2. Can it run read-only?
3. Does it need terminal access?
4. Does it need file write access?
5. Does it need external delivery?
6. Could it leak secrets?
7. Could it spam users?
8. How can we pause or remove it?
9. What manual test proves it works?
10. What requires human approval?
