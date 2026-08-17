# cachy-update

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/cachy-update) [![KDE Eco](https://img.shields.io/badge/KDE%20Eco-certified-brightgreen?logo=kde&logoColor=white&style=flat-square)](https://eco.kde.org/) [![Blue Angel](https://img.shields.io/badge/Blue%20Angel-DE--UZ%20215-0055a4?style=flat-square)](https://www.blauer-engel.de/en/certification/criteria) [![Energy](https://api.green-coding.io/v1/ci/badge/get?repo=Interested-Deving-1896%2Fcachy-update&branch=main&workflow=eco-audit.yml)](https://metrics.green-coding.io/ci-index.html)


<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/cachy-update.git
cd cachy-update
```

## Usage


The usage consist of starting [the systray applet](#the-systray-applet) and enabling [the systemd timer](#the-systemd-timer).

### The systray applet

To start the systray applet, launch the "Arch-Update Systray Applet" application from your app menu.

**Note:** GNOME shell does not support systray icons natively, GNOME users need to install the ["AppIndicator and KStatusNotifierItem Support" extension](https://extensions.gnome.org/extension/615/appindicator-support/) for the systray applet to show.

To start it automatically at boot, you can either:

- Run the following command (preferred method for most Desktop Environments, uses [XDG Autostart](https://wiki.archlinux.org/title/XDG_Autostart)):

```bash
arch-update --tray --enable
```

- Enable the associated systemd service (in case your Desktop Environment doesn't support [XDG Autostart](https://wiki.archlinux.org/title/XDG_Autostart)):

```bash
systemctl --user enable --now arch-update-tray.service
```

- Add the following command to your "auto-start" apps / configuration file (in case you use a Window Manager or a Wayland Compositor):

```bash
arch-update --tray
```

**If the systray applet doesn't start at boot regardless or if it doesn't work as expected** (e.g the icon is missing or the click actions do not act as they should), please read [this chapter](#the-systray-applet-does-not-start-at-boot-or-does-not-work-as-expected).

The systray icon dynamically changes to indicate the current state of your system ('up to date' or 'updates available'). When clicked, it launches `arch-update` in a terminal window via the [arch-update.desktop](https://github.com/CachyOS/cachy-update/blob/main/res/desktop/arch-update.desktop) file.

**If clicking the systray applet does nothing**, please read [this chapter](#run-cachy-update-in-a-specific-terminal-emulator).

### The systemd timer

To perform automatic and periodic checks for available updates, enable the associated systemd timer:

```bash
systemctl --user enable --now arch-update.timer
```

By default, a check is performed **at boot and then once every hour**. The check cycle can be customized, see [this chapter](#modify-the-check-cycle).

### Screenshots

Once started, the systray applet appears in the systray area of your panel.
It is the icon at the right of the 'coffee cup' one in the screenshot below:

![icon](https://github.com/user-attachments/assets/bf00781e-7ca6-46a9-a87e-c75f136e075d)

With [the systemd timer](#the-systemd-timer) enabled, checks for updates are automatically and periodically performed, but you can manually trigger one from the systray applet icon by right-clicking it and then clicking on the `Check for updates` menu entry. You can also see timestamps report for the last and next update checks:

![check_for_updates](https://github.com/user-attachments/assets/499a4072-fc79-43fe-aa0d-83f722575f24)

If there are new available updates, the systray icon shows a red circle and a desktop notification indicating the number of available updates is sent. You can directly run Cachy-Update from it or close / dismiss it thanks to the related click actions:

![notif](https://github.com/user-attachments/assets/6f1e2adf-112c-473b-85c7-18c592c3c47c)

You can see the list of available updates from the menu by right-clicking the systray icon.
A dropdown menu displaying the number and the list of pending updates is dynamically created for each sources that have some (Packages, AUR, Flatpak).
A "All" dropdown menu gathering the number and the list of pending updates for all sources is dynamically created if at least 2 different sources have pending updates:

*Clicking on the entry for a package opens the upstream project's URL in your web browser (except for Flatpak packages).*

![all](https://github.com/user-attachments/assets/da71e090-d06c-4640-9c00-5240ec7d0cdf)

![packages](https://github.com/user-attachments/assets/e40029d7-15f6-4e2a-928a-57dbd761b93d)

![aur](https://github.com/user-attachments/assets/23231347-9286-407a-88b9-74e779491406)

When the systray icon is left-clicked, `arch-update` is run in a terminal window (alternatively, you can click the "*X* update(s) available" entry or the dedicated "Run Cachy-Update" one from the right-click menu):

![run](https://github.com/user-attachments/assets/f10d07d3-3d38-483c-91e0-c41d1971e33a)

If at least one Arch Linux news has been published since the last run, `Cachy-Update` will offer you to read the latest Arch Linux news directly from the terminal window.
The news published since the last run are tagged as `[NEW]`:

![news](https://github.com/user-attachments/assets/93a0f89a-632b-46b5-88ba-9cabbe136963)

If no news has been published since the last run, `Cachy-Update` directly asks for your confirmation to proceed with update.

From there, just let `Cachy-Update` guide you through the various steps required for a complete and proper update of your system! :smile:

Certain options can be enabled, disabled or modified via the `arch-update.conf` configuration file. See the [arch-update.conf(5) man page](https://raw.githubusercontent.com/CachyOS/cachy-update/refs/heads/main/doc/man/arch-update.conf.5.scd) for more details.

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/cachy-update`](https://github.com/Interested-Deving-1896/cachy-update) and mirrored through:

```
Interested-Deving-1896/cachy-update  ──►  OpenOS-Project-OSP/cachy-update  ──►  OpenOS-Project-Ecosystem-OOC/cachy-update
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream influences recorded._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## Accessibility

<!-- AI:start:accessibility -->
This repo uses automated accessibility auditing via `check-accessibility.yml`.

Checks include: CODEOWNERS ownership coverage, README screen-reader compatibility,
WCAG 2.1 AA HTML compliance, audio overview (espeak-ng), and Braille output (liblouis).




Run the [Check Accessibility](https://github.com/Interested-Deving-1896/cachy-update/actions/workflows/check-accessibility.yml)
workflow to generate the first report and accessibility artifacts.
See [DOCS/accessibility.md](https://github.com/Interested-Deving-1896/cachy-update/blob/main/DOCS/accessibility.md) for the full reference.
<!-- AI:end:accessibility -->

## License

<!-- AI:start:license -->
[GPL-3.0](https://github.com/Interested-Deving-1896/cachy-update/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
