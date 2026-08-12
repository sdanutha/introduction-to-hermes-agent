# 4. Profiles in Dashboard

## Goal

Create two profiles and switch between them.

A profile has its own model, skills, memory, and sessions.

## Open Dashboard

```powershell
hermes dashboard
```

Open **Profiles**.

## Create a profile

Create:

```text
Name: training-researcher
Description: Finds public sources and writes short notes.
```

Create another profile:

```text
Name: training-writer
Description: Writes short summaries from given facts.
```

## Try the profiles

Switch to `training-researcher`:

```text
Find three official sources about Hermes.
Return the links and one point for each source.
```

Switch to `training-writer`:

```text
Write a short summary from these facts.
Use simple English.
```

## Important

- Profiles keep Hermes data separate.
- A profile is not a file sandbox.
- Use a safe terminal backend for risky work.

## Finish check

- Two profiles exist.
- The learner can switch profiles.
- Each profile has a different purpose.
