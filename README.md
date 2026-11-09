# Clamshell for Mac

Clamshell for Mac is a $9.99 menu bar app that keeps an Apple Silicon MacBook awake with the lid closed, with no external display or admin rights.

Clamshell is a closed-source, paid app. This repository holds its public issue tracker, changelog and documentation. It contains no app source code. Download the app from [clamshell.dev](https://clamshell.dev), Setapp or Homebrew.

[![Latest release](https://img.shields.io/github/v/release/matyasrathonyi/clamshell-for-mac?label=version)](https://github.com/matyasrathonyi/clamshell-for-mac/releases)
![macOS 14 or later](https://img.shields.io/badge/macOS-14%2B-black)
![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-required-black)

## Install

| Where | How | Price |
|---|---|---|
| Direct | Download from [clamshell.dev](https://clamshell.dev) | 7-day free trial with no card, then $9.99 once for one Mac or $19.99 for up to three |
| Homebrew | `brew install --cask clamshell` | Same trial and license as the direct download |
| Setapp | Search for Clamshell in [Setapp](https://setapp.com/apps/clamshell) | Included with a Setapp membership |

Every purchase has a 14-day money-back guarantee. There is no subscription. Version 1 owners upgrade to 2.0 for free. Clamshell is not on the Mac App Store; an App Store app with the same name is unrelated.

Requirements: an Apple Silicon Mac laptop on macOS 14 or later.

## What it does

- Close the lid and the Mac keeps working: builds, downloads, terminal sessions and coding agents keep running.
- No external display, dock or HDMI dummy plug needed.
- No admin password or sudo for the core app. A few optional modules use a helper you approve once in Login Items.
- Works on battery and on power, and stays armed when you plug in or unplug.
- Safety first: Clamshell lets the Mac sleep at 20% battery when on battery power (a switch, on by default), and disarms if macOS reports serious thermal pressure. Restarting always restores normal lid sleep.

Arm it from the menu bar, with Option + close lid, with Option + Option, by right-clicking the menu bar icon, from Shortcuts, or with a `clamshell://` URL from a script.

## Who it is for

- People who run Claude Code, Codex or other coding agents for hours and want to close the lid and walk away.
- Developers with long builds, test runs or local servers.
- Anyone finishing a big download, upload or backup in a bag, on a couch or overnight.
- A MacBook used as a home server, lid closed.

## Use it with Claude Code and Codex

Version 2.0 adds optional agent modules, one switch each in Settings:

- **Agent Status**: see what your Claude Code and Codex agents are doing from the menu bar.
- **Agent Notifications**: know when an agent needs you or is done.
- **Finish Work, Then Sleep**: let your agents finish, then let your Mac sleep.
- **Sleep Until Reset**: sleep through a usage limit and wake when it resets.
- **Agent Screen**: agents can use the screen with the lid closed (off by default).
- **Agent Light**: your agents' state on a light you can see across the room.

Agents and scripts can also arm and disarm Clamshell directly:

```sh
open "clamshell://arm"      # before a long job
open "clamshell://disarm"   # when it is done
```

See [docs/agents.md](docs/agents.md) for an agent-ready guide and [docs/url-commands.md](docs/url-commands.md) for every URL command.

## Modules

Clamshell 2.0 has more than 30 optional modules, grouped as Agents, Keyboard, Sound, Power, Time, Awake, Sessions, Security, Triggers and Custom. Examples: Arm on a Schedule, Arm While an App Runs, Battery Budget, Home Server, Quiet Close, Bag Check and Password After Close. With Make Your Own, you describe a module to Claude Code, Codex or Cursor and it builds one. Clamshell works fully without any module, and every module is included in the one-time purchase. Full list: [clamshell.dev/modules](https://clamshell.dev/modules).

## How it compares

Facts below come from each product's own website, App Store listing or README, as checked on clamshell.dev in October 2026. Prices and features change; check the vendor before you decide. The full write-ups, with sources, are linked in the last column.

| Option | Lid closed, no external display | Price | Admin at install | More |
|---|---|---|---|---|
| Clamshell | Yes, on battery or power | 7-day trial, then $9.99 once | No, for the core app | [What Clamshell is](https://clamshell.dev/guides/what-is-clamshell) |
| `caffeinate` (built into macOS) | No. It stops idle sleep; closing the lid still sleeps the Mac | Free | No | [Why caffeinate stops at the lid](https://clamshell.dev/guides/why-caffeinate-does-not-work-lid-closed) |
| Apple's closed-display mode | No. It needs an external display, keyboard and power attached | Free with the hardware | No | [Clamshell mode without a display](https://clamshell.dev/guides/clamshell-mode-without-external-display) |
| Amphetamine | Yes, with its Closed-Display Mode and the Power Protect add-on on Apple Silicon laptops | Free | Yes, for the add-on | [Amphetamine alternative](https://clamshell.dev/guides/amphetamine-alternative-lid-closed) |
| KeepingYouAwake | No, per its README | Free, open source | No | [KeepingYouAwake and the lid](https://clamshell.dev/guides/keepingyouawake-lid-closed) |
| Sleepless | Yes, on battery too | Free, open source (MIT), needs macOS 26 | Yes | [Sleepless vs Clamshell](https://clamshell.dev/guides/clamshell-vs-sleepless) |
| LidRun | Yes, in the Pro tier; also supports Intel Macs | Free lid-open tier, Pro from $9.90 once | Yes, until its helper is approved | [LidRun vs Clamshell](https://clamshell.dev/guides/clamshell-vs-lidrun) |

If the lid stays open, almost any keep-awake tool works, including the free ones. Clamshell is for when the lid closes. More comparisons: [clamshell.dev/guides/compare](https://clamshell.dev/guides/compare).

## FAQ

### How do I keep my MacBook awake with the lid closed and no monitor?

Install Clamshell, arm it from the menu bar (or hold Option while you close the lid), and close the lid. The Mac keeps working with the built-in display off. No external display, dock or dummy plug is needed.

### Does Clamshell need an external display?

No. macOS normally needs an external display before the lid can close without sleep; Clamshell removes that. If a monitor is connected, closing the lid also keeps the Mac awake, even on battery.

### Does it need sudo or an admin password?

No for the core app. The optional modules Low Power While Closed, Fan Boost, Agent Light, Sleep Until Reset, Sleep Means Sleep, Stay Off When Opened and Password After Close use a helper you approve once in Login Items. They stay off until you turn them on.

### Will Claude Code or Codex keep running with the lid closed?

Yes, while Clamshell is armed. Agents, terminal sessions, builds and downloads keep running, and the Mac stays on the network for SSH and Screen Sharing. Guides: [Claude Code](https://clamshell.dev/guides/keep-claude-code-running-lid-closed), [Codex](https://clamshell.dev/guides/keep-codex-running-lid-closed), [agents overnight](https://clamshell.dev/guides/run-ai-agents-overnight-macbook).

### Does it work on battery?

Yes. It works the same on battery and stays armed when you plug in or unplug. On battery power, a switch that is on by default lets the Mac sleep at 20% instead of running flat. See [running a MacBook lid closed on battery](https://clamshell.dev/guides/macbook-lid-closed-on-battery).

### Is it safe to run a MacBook with the lid closed?

The Mac runs as it would with the lid open. If macOS reports serious or critical thermal pressure, Clamshell disarms and the Mac goes back to normal sleep. Bag Check, an optional module, warns you if your Mac did not sleep in your bag. More in [is it safe to run a MacBook lid closed](https://clamshell.dev/guides/is-it-safe-to-run-macbook-lid-closed).

### Does it work on Intel Macs?

No. Clamshell needs an Apple Silicon Mac laptop on macOS 14 or later. Arming with Option + close lid needs a lid angle sensor: MacBook Air M2 (2022) or later, or the 14-inch and 16-inch MacBook Pro (2021) or later. Every other way to arm works on all supported Macs.

### How do I stop it?

Disarm from the menu bar, run `open "clamshell://disarm"`, or quit the app. Normal lid sleep comes back. Arming with Option + close lid, Option + Option or a right-click lasts for the next close only.

### Is there a free trial?

Yes, 7 days from download with no card. Then $9.99 once for one Mac or $19.99 for up to three. [Pricing](https://clamshell.dev/pricing).

### Is Clamshell on Setapp?

Yes, with every module. Clamshell is also installable with `brew install --cask clamshell`.

### Is Clamshell open source?

No. Clamshell is a closed-source paid app. This repository holds the issue tracker, changelog and documentation only.

## Support

- Bugs and feature requests: [open an issue](https://github.com/matyasrathonyi/clamshell-for-mac/issues/new/choose).
- First steps when something is off: [docs/troubleshooting.md](docs/troubleshooting.md).
- Private help, licenses and refunds: email [hello@clamshell.dev](mailto:hello@clamshell.dev). In Clamshell, Settings > General > Copy diagnostics for support puts a support report on your clipboard; paste it into the email, not into a public issue.
- Security reports: see [SECURITY.md](SECURITY.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md), [Releases](https://github.com/matyasrathonyi/clamshell-for-mac/releases) and [clamshell.dev/changelog](https://clamshell.dev/changelog). Releases here are notes only; the app is downloaded from clamshell.dev, Setapp or Homebrew.

## License

The documentation in this repository is licensed under [CC BY 4.0](LICENSE). The Clamshell app, its name and its icons are proprietary and are not covered by that license.
