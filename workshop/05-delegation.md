# 5. Delegation

## Description

Delegation lets Hermes give small tasks to other agents. It is good for parallel research and separate work streams.

## Goal

Give small tasks to other agents.

Use this after the basic Desktop workflow works.

## Setup

Use delegation after the basic workflow works.

### Simple idea

```text
One big task
-> Small tasks
-> Other agents
-> One checked result
```

## Try it

### Prompt

```text
Delegate three small research tasks:

1. Find the official Hermes page for Profiles.
2. Find the official Hermes page for Skills.
3. Find the official Hermes page for Kanban.

For each task, return:
- The URL
- Two short points

Use official Hermes docs.
Then make one short table.
```

## Check the result

### What to notice

- Each agent starts with a new chat.
- Give each agent a clear goal.
- Give enough context.
- Check important results.

### Task pattern

```text
Goal: What do you need?
Context: What should the agent know?
Check: How will you check the result?
```

## Safety

- Check delegated results before using them.
- Do not give agents private data unless needed.

## Finish check

- Tasks are small.
- Each task has a clear goal.
- The main agent checks the result.

## Official guide

- https://hermes-agent.nousresearch.com/docs/user-guide/features/delegation/
