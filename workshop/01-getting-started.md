# 1. Getting Started with Hermes

## Description

This section explains how to install Hermes and start a basic chat. It is good for new users.

## Goal

Install Hermes, complete basic setup, and start your first chat.

## Setup

### Install Hermes

Install Hermes Desktop for Windows:

- https://hermes-agent.nousresearch.com/docs/getting-started/installation

For command line only, run this in PowerShell:

```powershell
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

### Set up Hermes

Fast setup with Nous Portal:

```powershell
hermes setup --portal
```

Or use the setup wizard:

```powershell
hermes setup
```

## Try it

### Start your first chat

```powershell
hermes
```

You can also try:

```powershell
hermes --tui
hermes --cli
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

### Try one simple chat

```text
Tell me what you can do.
```

## Check the result

### Basic commands

| Command | Use it to |
| --- | --- |
| `hermes --help` | See all commands. |
| `hermes` | Start a chat. |
| `hermes --tui` | Launch the modern TUI. |
| `hermes --cli` | Force the classic REPL. |
| `hermes setup` | Run setup wizard. |
| `hermes model` | Select default model. |
| `hermes sessions list` | List past sessions. |
| `hermes --resume <session_id>` | Resume a specific session by ID. |
| `hermes desktop` | Start the Desktop App. |
| `hermes dashboard` | Start the Dashboard Web. |

## Finish check

- Hermes is installed.
- Setup is complete.
- A model answers.
- The learner knows the basic commands.

## Safety

- Do not save passwords, API keys, or secrets.

## Official guide

- https://hermes-agent.nousresearch.com/docs/getting-started/installation
- https://hermes-agent.nousresearch.com/docs/getting-started/quickstart
- https://hermes-agent.nousresearch.com/docs/reference/cli-commands
