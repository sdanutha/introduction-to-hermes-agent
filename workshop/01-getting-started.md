# 1. Getting Started with Hermes

## Goal

Install Hermes, complete basic setup, and start your first chat.

## 1. Install Hermes

Install Hermes Desktop for Windows:

- https://hermes-agent.nousresearch.com/docs/getting-started/installation

For command line only, run this in PowerShell:

```powershell
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

## 2. Set up Hermes

Fast setup with Nous Portal:

```powershell
hermes setup --portal
```

Or use the setup wizard:

```powershell
hermes setup
```

## 3. Check your setup

```powershell
hermes doctor
hermes model
hermes tools
```

## 4. Start your first chat

```powershell
hermes
```

You can also try:

```powershell
hermes --tui
```

### Prompt 1: Interview me

```text
I want you to interview me.

Ask one question at a time.
Wait for my answer before the next question.

Learn about:
- My work
- My regular tasks
- My goals
- How I create content or do research
- How I make decisions
- The apps and websites I use
- Tasks that take too much time
- Tasks I avoid or want help with

When we finish:
1. Summarize what you learned.
2. Suggest useful information to save in memory.
3. Ask for my approval.
4. Save only stable and useful information.
5. Do not save passwords, API keys, or secrets.
```

## 5. Try one simple chat

```text
Tell me what you can do.
```

## Basic commands

| Command | Use it to |
| --- | --- |
| `hermes` | Start a chat. |
| `hermes --help` | See all commands. |
| `hermes --tui` | Start the modern text interface. |
| `hermes --cli` | Start the classic CLI. |
| `hermes setup` | Change setup. |
| `hermes model` | Choose a model. |
| `hermes doctor` | Find setup problems. |
| `hermes tools` | Check or change tools. |
| `hermes --continue` | Continue the last session. |
| `hermes sessions list` | See past sessions. |
| `hermes --resume <session_id>` | Resume a selected session. |
| `hermes desktop` | Open Desktop. |
| `hermes dashboard` | Open Dashboard. |

## If something fails

Run these commands:

```powershell
hermes setup
hermes model
hermes doctor
```

More commands:

- https://hermes-agent.nousresearch.com/docs/reference/cli-commands

## Finish check

- Hermes is installed.
- Setup is complete.
- A model answers.
- The learner knows the basic commands.
