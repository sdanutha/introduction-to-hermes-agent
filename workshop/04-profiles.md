# 4. Profiles

## Description

A profile is a separate Hermes assistant with its own settings, memory, skills, and sessions. It is good for different roles.

## Goal

Create two profiles and switch between them.

A profile has its own model, skills, memory, and sessions.

## Setup

### Open Profiles

You can manage profiles in Desktop, Dashboard, or CLI.

In Desktop or Dashboard, open **Profiles**.

In CLI, run:

```powershell
hermes profile list
```

## Try it

### Create a profile

Create:

```text
Name: researcher-agent
Description: Finds public sources and writes short notes.
```

Create another profile:

```text
Name: writer-agent
Description: Writes short summaries from given facts.
```

### Try the profiles

Switch to `researcher-agent`:

```text
Find three official sources about Hermes.
Return the links and one point for each source.
```

Switch to `writer-agent`:

```text
Write a short summary from these facts.
Use simple English.
```

### Create a profile with a prompt

You can also ask Hermes to create a profile for you.

Try this prompt:

```text
Please create a profile that is an expert in date and time.
When I ask about the date or time, please provide the time in both Singapore and the US.
```

Review the profile name and settings before you use it.

## Check the result

- Profiles keep Hermes data separate.
- A profile is not a file sandbox.

## Safety

- Review the profile settings before use.
- Do not add passwords or API keys to a profile prompt.

## Finish check

- Two profiles exist.
- The learner can switch profiles.
- Each profile has a different purpose.

## Official guide

- https://hermes-agent.nousresearch.com/docs/user-guide/profiles/
