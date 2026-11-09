# Changelog

User-facing changes to Clamshell for Mac. This file mirrors the app's own changelog, which is also published at [clamshell.dev/changelog](https://clamshell.dev/changelog). The format follows [Keep a Changelog](https://keepachangelog.com/), and versions follow [Semantic Versioning](https://semver.org/).

Earlier 1.x versions are listed on [clamshell.dev/changelog](https://clamshell.dev/changelog).

## [2.0.0] - 2026-11-09

### Added

- A new app icon and menu bar icon, hand-drawn from one shell stroke. Armed and paused sessions change only the menu bar icon's color.
- Press both Option keys together (Option + Option) to arm for the next close. It is on by default and needs no extra permission.
- Modules: optional extras in a new Modules section of Settings, one switch each. Browse them as cards, search them and filter by group. Each has its own icon, its own page and a short walkthrough the first time you turn it on. Clamshell works fully without any of them, and its safety rules always come first.
- Agents: Agent Screen (agents can use the screen with the lid closed), Agent Status (see what your Claude Code and Codex agents are doing from the menu bar), Agent Notifications (know when an agent needs you or is done), Finish Work, Then Sleep (let your agents finish, then let your Mac sleep), Agent Light (your agents' state on a light you can see across the room) and Sleep Until Reset (sleep through a usage limit and wake when it resets).
- Keyboard: Caps Lock (Caps Lock becomes an arm switch, and its light shows when your Mac stays awake) and Cleaning Lock (lock the keyboard and trackpad while you wipe them).
- Sound: Lid-Close Sound (eight new sounds, a preview on every choice and its own volume) and Quiet Close (closing the lid mutes your Mac; opening it brings the sound back).
- Power: Always On While Plugged In, Home Server (always armed, lid closed, for a Mac that serves), Battery Budget (a closed session uses only the battery you allow, then sleeps), Low Power While Closed, Fan Boost (full fan speed while your Mac is closed), Bluetooth Off While Closed, Sleep Means Sleep (no Power Nap or network wakes while asleep on battery) and Stay Off When Opened (a shut-down Mac stays off when you open the lid or plug it in).
- Time: Sleep Timer (your Mac goes to sleep after a set time, fading the music out) and Sleep When Idle (a closed Mac sleeps once nothing is working).
- Awake: Keep Awake (keep your Mac awake with the lid open, indefinitely, for a set time or while your agents work), Awake While Connected (stays awake while you're connected over SSH or Screen Sharing) and Finish Jobs, Then Sleep (let downloads, exports and backups finish, then let your Mac sleep).
- Sessions: Bag Check (warns you if your Mac didn't sleep in your bag), Eject on Sleep (your external drives eject when your closed Mac sleeps) and Lid Shortcuts (run your own shortcuts when you close and open the lid).
- Security: Password After Close (close the lid and the next unlock needs your password).
- Triggers: Arm While an App Runs, Arm on a Wi-Fi Network, Arm on a Schedule and Arm When a Drive Connects. Clamshell arms by itself while an app you choose runs, on the Wi-Fi network you choose, during the hours you choose, or while a drive you choose is connected.
- Make Your Own: describe a module to any AI coding agent (Claude Code, Codex, Cursor) and it builds one, with its own icon, a description you edit in place and rules that keep your Mac awake or end the session. It appears in the new Custom group.
- Permissions a module needs open a small floating guide under System Settings: drag Clamshell into the list and it closes by itself.

### Changed

- A redesigned Settings window that can be resized.
- Right-clicking the menu bar icon now arms for the next close only. Every way to arm is always on: Option + close lid, Option + Option and right-click.
- Option + Option replaces the Control-Option-Command-L shortcut.
- Disarm on low battery lives in General and always triggers at 20% on battery power. It never disarms while plugged in.
- Agent Screen is off by default, so Clamshell turns the display off on close unless you turn it on.
- An external display no longer pauses Clamshell. With a monitor connected, closing the lid keeps your Mac awake, even on battery. With a TV, projector or AirPlay mirroring your screen, closing the lid keeps the picture there, and opening the lid afterwards locks your Mac.
- The closing animation always plays, except when Reduce Motion is on.
- The `configure` automation URL now accepts only `lowBatteryDisarm`. Scripts that set the arming methods or the low-battery threshold get an error naming the setting that no longer exists.
- The first time you open Settings, Clamshell asks once to show its notifications as banners.
- The optional survey after you buy adds "GitHub or a forum" and "A developer tool" as answers, then asks one more optional question: what made you buy. You can close it at any point.

