# Clamshell URL commands

Clamshell for Mac answers a small set of `clamshell://` URLs, so scripts, coding agents, launchers and Shortcuts can arm and disarm it. Open them with `open` in Terminal, from any app that opens links, or with the Open URLs action in Shortcuts.

This page covers Clamshell 2.0 and later.

## Which scheme to use

| Edition | Scheme |
|---|---|
| Direct download from clamshell.dev, and Homebrew | `clamshell://` |
| Setapp | `clamshell-setapp://` |

Every example below uses `clamshell://`. On the Setapp edition, replace it with `clamshell-setapp://`, for example `open "clamshell-setapp://arm"`.

## Commands

| URL | What happens |
|---|---|
| `clamshell://arm` | Arms Clamshell. Close the lid and the Mac stays awake. Armed this way, Clamshell stays on until you disarm. |
| `clamshell://disarm` | Disarms Clamshell. Normal lid sleep comes back. |
| `clamshell://toggle` | Disarms if armed, arms if not. |
| `clamshell://settings` | Opens the Clamshell Settings window. Takes no parameters. |
| `clamshell://configure?lowBatteryDisarm=true` | Turns on "Disarm on low battery" (lets the Mac sleep at 20% on battery power). |
| `clamshell://configure?lowBatteryDisarm=false` | Turns that switch off. |
| `clamshell://activate?key=YOUR-LICENSE-KEY` | Activates a license key. Direct edition only; the Setapp edition has no license keys. |

The command name is not case-sensitive, and `clamshell:///arm` (three slashes) works the same as `clamshell://arm`.

## Examples

```sh
# Arm before a long job, disarm when it ends
open "clamshell://arm"
./run-long-job.sh
open "clamshell://disarm"

# Open Settings
open "clamshell://settings"

# Keep the low-battery safety switch on
open "clamshell://configure?lowBatteryDisarm=true"
```

## What to expect

- **The request is asynchronous.** `open` returns as soon as macOS hands the URL to Clamshell. Check that the menu bar icon shows Clamshell as armed before you close the lid.
- **`arm`, `disarm` and `toggle` are silent.** They show no alert when Clamshell declines, so a script cannot tell from the exit code of `open` whether arming worked. When you need a clear result, use the Shortcuts actions below.
- **Asking for the state it is already in is fine.** Arming an armed Clamshell, or disarming a disarmed one, changes nothing.
- **`configure` shows an alert when it cannot apply a change**, titled "Clamshell settings were not changed", with the reason.

## Why an arm can be declined

| Reason | What to do |
|---|---|
| The trial has ended and no license is active (direct edition) | Buy a license or activate your key, then try again. |
| macOS reports high thermal pressure | Let the Mac cool, then try again. |
| Always On While Plugged In is set not to arm on battery | Plug in the Mac, or change that module's setting. |
| One of your modules declined the request | Check the modules you have turned on in Settings. |
| Clamshell is still starting | Wait a moment and try again. |

## `configure` errors

`configure` accepts exactly one setting, `lowBatteryDisarm`, with the value `true` or `false` in lowercase.

| Request | Result |
|---|---|
| `clamshell://configure` with no setting | Error: choose at least one setting. |
| An unknown setting name | Error naming the setting Clamshell does not recognize. |
| `lowBatteryThreshold`, `lidCloseArming`, `rightClickArming` or `shortcutArming` | Error saying the setting no longer exists. These were removed in 2.0: every way to arm is always on, and the low-battery level is fixed at 20%. |
| The same setting twice | Error: provided more than once. |
| A missing value, or a value other than `true` or `false` | Error naming the setting. |
| No active trial or license | Direct edition: Clamshell asks for a license. Setapp edition: an alert asks for an active Setapp subscription. |

When an error appears, nothing is changed.

## Shortcuts actions

Clamshell adds four actions to the Shortcuts app: **Arm Clamshell**, **Disarm Clamshell**, **Toggle Clamshell** and **Clamshell Status**.

- Clamshell Status reports whether Clamshell is armed or disarmed.
- Unlike the URLs, the arm and disarm actions fail visibly when Clamshell declines. A shortcut you run with `shortcuts run "My Shortcut Name"` from Terminal then exits with a non-zero status and a readable message, so scripts and agents can check the result.

## More

- Using Clamshell from a coding agent: [agents.md](agents.md)
- Something not working: [troubleshooting.md](troubleshooting.md)
- Claude Code hooks that arm and disarm Clamshell: [clamshell.dev/guides/claude-code-hooks-keep-mac-awake](https://clamshell.dev/guides/claude-code-hooks-keep-mac-awake)
