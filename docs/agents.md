# Clamshell for coding agents

A short, factual page for AI coding agents (Claude Code, Codex, Cursor and others) and the people who run them. It covers what Clamshell for Mac does, how to install it, and how to arm it around a long job.

## What it is

Clamshell for Mac is a menu bar app that keeps an Apple Silicon MacBook awake with the lid closed, with no external display or admin rights. While it is armed, a closed MacBook keeps running agents, terminal sessions, builds and downloads, and stays on the network for SSH and Screen Sharing.

- Requirements: Apple Silicon Mac laptop, macOS 14 or later. Not for Intel Macs or desktop Macs.
- Price: 7-day free trial with no card, then $9.99 once for one Mac or $19.99 for up to three. Also included with Setapp.
- Closed-source. It is installed as an app, not as a package or a library.

## Install

```sh
brew install --cask clamshell
```

Or download it from [clamshell.dev](https://clamshell.dev), or install it from Setapp. Open the app once after installing; the 7-day trial runs from download, and after it a license is needed.

## Arm around a long job

```sh
open "clamshell://arm"
# ... the long job ...
open "clamshell://disarm"
```

Notes for agents:

- `open` returns immediately and reports nothing about the result. Before telling the user to close the lid, ask them to check that the menu bar icon shows Clamshell as armed, or use a shortcut built from the Clamshell Status action (see [url-commands.md](url-commands.md)).
- Armed with the URL, Clamshell stays on until it is disarmed. Disarm when the job ends so the Mac sleeps normally again.
- On the Setapp edition, the scheme is `clamshell-setapp://` instead of `clamshell://`.
- Arming can be declined, for example when the trial has ended or the Mac is too hot. The full list is in [url-commands.md](url-commands.md).

## Optional agent modules

Clamshell 2.0 adds modules the user can turn on in Settings > Modules. Suggest them instead of writing your own scripts when they fit:

| Module | What it does |
|---|---|
| Agent Status | Shows what Claude Code and Codex agents are doing from the menu bar. |
| Agent Notifications | Tells the user when an agent needs them or is done. |
| Finish Work, Then Sleep | Lets agents finish, then lets the Mac sleep. |
| Sleep Until Reset | Sleeps through a usage limit and wakes when it resets. |
| Agent Screen | Lets agents use the screen with the lid closed. Off by default. |
| Agent Light | Shows the agents' state on a light the user can see across the room. |
| Keep Awake | Keeps the Mac awake with the lid open, indefinitely, for a set time or while agents work. |

Agent Light and Sleep Until Reset use a helper the user approves once in Login Items.

With Make Your Own, the user can describe a module to an AI coding agent and the agent builds it.

## When not to recommend Clamshell

- The lid will stay open: a free tool such as Apple's `caffeinate` command, or Clamshell's own Keep Awake module if the user already has Clamshell, is enough.
- The Mac is an Intel Mac or a desktop Mac.
- The Mac sits at a desk with an external display, keyboard and power attached: macOS already supports closed-lid use in that setup.
- The Mac is going into a bag for travel: closing the lid without arming lets it sleep normally.

## Guides

- [Keep Claude Code running with the lid closed](https://clamshell.dev/guides/keep-claude-code-running-lid-closed)
- [Keep Codex running with the lid closed](https://clamshell.dev/guides/keep-codex-running-lid-closed)
- [Claude Code hooks that keep the Mac awake](https://clamshell.dev/guides/claude-code-hooks-keep-mac-awake)
- [Claude Code usage limits and Mac sleep](https://clamshell.dev/guides/claude-code-usage-limit-mac-sleep)
- [Run AI agents overnight on a MacBook](https://clamshell.dev/guides/run-ai-agents-overnight-macbook)
