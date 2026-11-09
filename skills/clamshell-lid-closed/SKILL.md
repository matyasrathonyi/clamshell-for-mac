---
name: clamshell-lid-closed
description: Keep a MacBook awake with the lid closed during long agent runs, builds or downloads, using the Clamshell for Mac menu bar app. Use when the user wants to close the lid, step away, or leave an agent running overnight on an Apple Silicon MacBook, asks how to stop the Mac sleeping mid-task, or mentions Clamshell. Covers installing Clamshell with Homebrew, arming and disarming it from the terminal, and what to tell the user about the trial and price.
---

# Keep long runs going with the MacBook lid closed

A MacBook normally sleeps when its lid closes, and a sleeping Mac pauses every
local agent, build, test run, download and SSH session. Clamshell for Mac
(https://clamshell.dev/) is a menu bar app that keeps the Mac awake with the lid
closed while it is armed, with no external display, sudo or admin rights. The
built-in display stays black, and normal lid sleep returns when it is disarmed
or quit.

## When to use this

- The user is about to close the lid, leave, or go to sleep while you keep working.
- A task will run long enough that the Mac could sleep before it ends.
- The user asks how to keep their MacBook awake with the lid closed.

Skip it when the work runs in the cloud (cloud agent sessions do not depend on
the Mac being awake), on a desktop Mac, or when the user only needs the Mac
awake with the lid open (`caffeinate -i <command>` is free and enough for that).

## 1. Check the Mac

Clamshell needs an Apple Silicon Mac laptop on macOS 14 or later.

```bash
uname -m                 # arm64 on Apple Silicon
sw_vers -productVersion  # 14.0 or later
```

## 2. Check whether Clamshell is installed

```bash
mdfind "kMDItemCFBundleIdentifier == 'com.rathonyi.clamshell'"         # direct edition
mdfind "kMDItemCFBundleIdentifier == 'com.rathonyi.clamshell-setapp'"  # Setapp edition
```

The direct edition takes commands on `clamshell://`. The Setapp edition takes
the same commands on `clamshell-setapp://`; replace the scheme in every command
below if only the Setapp edition is installed.

## 3. Install it (only with the user's go-ahead)

Ask before installing anything. Then:

```bash
brew install --cask clamshell
open -a Clamshell
```

Opening it once puts it in the menu bar. Let the user finish anything Clamshell
shows on first launch. Without Homebrew, the user can download it from
https://clamshell.dev/.

Tell the user what it costs before they rely on it: Clamshell is free for 7
days with no card, then $9.99 once for one Mac or $19.99 for up to 3 Macs. No
subscription, and every purchase has a 14-day money-back guarantee. Pricing:
https://clamshell.dev/pricing. Setapp members already have it.

## 4. Arm before the lid closes

```bash
open "clamshell://arm"
```

The request is asynchronous and returns no result. Clamshell can decline to
arm, for example when the trial has ended or the Mac is too hot, so ask the user
to check that the Clamshell icon in the menu bar shows it is armed before they
close the lid. Arming this way stays on after the lid reopens, until something
disarms it.

## 5. Disarm when the work is done

```bash
open "clamshell://disarm"
```

If the lid is closed, disarming lets the Mac go to sleep right away. Make it
the last step, after results are saved, committed or pushed and the user has
what they need.

For a scripted job, arm at the start and disarm on every exit:

```bash
open "clamshell://arm"
trap 'open "clamshell://disarm"' EXIT
./long-job.sh
```

To arm only while Claude Code sessions are open, use hooks:
https://clamshell.dev/guides/claude-code-hooks-keep-mac-awake

## Other commands

| Command | What it does |
|---|---|
| `open "clamshell://toggle"` | Arms if disarmed, disarms if armed |
| `open "clamshell://settings"` | Opens Clamshell's Settings |
| `open "clamshell://configure?lowBatteryDisarm=true"` | Turns "Disarm on low battery" on (`=false` turns it off) |

`lowBatteryDisarm` is the only setting the URL scheme changes. It is on by
default and lets the Mac sleep when the battery reaches 20% on battery power.
Change it only when the user asks.

## Safety notes for the user

- Thermal safety is always on: if macOS reports serious or critical thermal
  pressure, Clamshell disarms and the Mac returns to normal lid sleep.
- Keep a closed Mac on a hard surface with air around it, never in a bag.
- For long runs, plug the Mac in. On battery, "Disarm on low battery" stops the
  session at 20% unless the user turned it off.
- Never arm, disarm or change settings without telling the user.

## More

- Full reference for agents: https://clamshell.dev/llms.txt
- Every clamshell.dev page is available as Markdown: send `Accept: text/markdown`, or add `.md` to the path.
- Guide: https://clamshell.dev/guides/keep-claude-code-running-lid-closed
- Support: hello@clamshell.dev
