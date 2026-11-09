# Troubleshooting Clamshell

Start here when Clamshell for Mac does not do what you expect. If none of this helps, email [hello@clamshell.dev](mailto:hello@clamshell.dev) with a support report (see the last section).

## First steps

1. **Update Clamshell.** Most fixes ship in updates. The latest version is on [clamshell.dev/changelog](https://clamshell.dev/changelog). Homebrew users can run `brew upgrade --cask clamshell`; Setapp updates through Setapp.
2. **Check your Mac.** Clamshell needs an Apple Silicon Mac laptop on macOS 14 or later.
3. **Quit and reopen Clamshell.** Then arm it again and check the menu bar icon before you close the lid.
4. **Restart the Mac** if something still looks stuck. A restart always restores normal lid sleep.

## The Mac slept when I closed the lid

- **Was Clamshell armed?** The menu bar icon changes color when Clamshell is armed. Arming with Option + close lid, Option + Option or a right-click on the menu bar icon lasts for the next close only, so arm again before the next close.
- **Option + close lid did nothing.** That gesture needs a lid angle sensor: MacBook Air M2 (2022) or later, or the 14-inch and 16-inch MacBook Pro (2021) or later. On other supported Macs, arm from the menu bar, with Option + Option or with a right-click.
- **Low battery.** On battery power, Clamshell lets the Mac sleep at 20% so it does not run flat. You can turn this off in Settings > General ("Disarm on low battery"). It never disarms while plugged in.
- **Heat.** If macOS reports serious or critical thermal pressure, Clamshell disarms and the Mac sleeps normally. Let it cool and give it some airflow.
- **A module ended the session.** Modules such as Battery Budget, Sleep Timer, Sleep When Idle, Finish Work, Then Sleep and Finish Jobs, Then Sleep are designed to let the Mac sleep. Check which modules are on in Settings > Modules.
- **The trial ended.** After 7 days the direct edition needs a license. [Pricing](https://clamshell.dev/pricing).

## A script or agent could not arm Clamshell

- Use the scheme for your edition: `clamshell://` for the direct download and Homebrew, `clamshell-setapp://` for Setapp.
- `open "clamshell://arm"` returns before Clamshell acts and shows nothing if arming is declined. Check the menu bar icon, or use a shortcut with the Arm Clamshell action, which reports a failure.
- Scripts written for 1.x that set the arming methods or the low-battery threshold with `configure` now get an error. Those settings were removed in 2.0. See [url-commands.md](url-commands.md).

## A module asks for a permission or approval

- Some modules need a macOS permission. Clamshell opens a small guide under System Settings: drag Clamshell into the list and the guide closes by itself.
- Low Power While Closed, Fan Boost, Agent Light, Sleep Until Reset, Sleep Means Sleep, Stay Off When Opened and Password After Close use a helper you approve once in Login Items in System Settings. Clamshell itself works without it.

## The Mac stays awake when I do not want it to

- Disarm from the menu bar or quit Clamshell. Normal lid sleep comes back.
- Check for modules that arm by themselves: Always On While Plugged In, Home Server, Arm While an App Runs, Arm on a Wi-Fi Network, Arm on a Schedule and Arm When a Drive Connects.
- Turn on Bag Check if you often put the Mac in a bag. It warns you if your Mac did not sleep.

## Sending a support report

In Clamshell, open Settings > General and use **Copy diagnostics for support** under Support. It copies a report to your clipboard; nothing is sent. Paste it into an email to [hello@clamshell.dev](mailto:hello@clamshell.dev).

Please do not paste the report, logs or Terminal output into a public GitHub issue. Email keeps them private.
