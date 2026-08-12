# Hermes Workshop Review

Review date: 2026-08-13

## Verdict

The workshop has a good beginner flow:

```text
Install -> Chat -> Tools -> Memory and Skills -> Automation
```

The updated workshop now uses Desktop first and Dashboard second.

## Important points

1. Use `hermes setup --portal` for the fastest setup when using Nous Portal.
2. Use `hermes --continue` to show that sessions can continue later.
3. Ask Hermes to save useful, stable memory. Do not save passwords or API keys.
4. A profile separates Hermes data, but it is not a file sandbox.
5. Cron needs a running gateway.
6. Kanban needs the gateway dispatcher.

## Good extra topics

- Try `hermes --tui`.
- Use `/help`, `/tools`, `/model`, and `/save`.
- Use a model with at least 64K context.
- Give delegated agents a clear goal, context, and check.
- Show how to pause or remove an automation job.

## Sources

- https://hermes-agent.nousresearch.com/docs/getting-started/installation
- https://hermes-agent.nousresearch.com/docs/getting-started/quickstart
- https://hermes-agent.nousresearch.com/docs/user-guide/features/tools
- https://hermes-agent.nousresearch.com/docs/user-guide/features/memory
- https://hermes-agent.nousresearch.com/docs/user-guide/features/skills
- https://hermes-agent.nousresearch.com/docs/user-guide/security
- https://hermes-agent.nousresearch.com/docs/user-guide/profiles/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/delegation/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/cron/
- https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban/
- https://hermes-agent.nousresearch.com/docs/reference/cli-commands
