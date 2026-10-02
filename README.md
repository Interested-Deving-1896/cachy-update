# cachy-update

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/cachy-update) [![KDE Eco](https://img.shields.io/badge/KDE%20Eco-certified-brightgreen?logo=kde&logoColor=white&style=flat-square)](https://eco.kde.org/) [![Blue Angel](https://img.shields.io/badge/Blue%20Angel-DE--UZ%20215-0055a4?style=flat-square)](https://www.blauer-engel.de/en/certification/criteria)


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


For desktop machines, the usage consist of starting [the systray applet](#the-systray-applet) and enabling [the automated update checks](#the-automated-update-checks).
For headless machines, `Cachy-Update` includes an extensive CLI.

### The systray applet

To start the systray applet and enable it automatically at boot, run the following command (preferred method for most environments, uses [XDG Autostart](https://wiki.archlinux.org/title/XDG_Autostart)):

```bash
cachy-update --tray --enable
```

In case your graphical environment doesn't support XDG Autostart, add the following command your environment auto-start method instead:

*Note that the small startup delay in the form of the `sleep 3` command may not always be required but acts as a useful trick to avoid eventual [race condition](https://en.wikipedia.org/wiki/Race_condition) issues which may lead to the systray applet unexpectedly not starting at boot. I therefore recommend its usage as a safety measure (this small delay is already applied by default with the XDG Autostart / `cachy-update --tray --enable` method).*

```bash
sleep 3 && cachy-update --tray
```

The systray icon dynamically changes to indicate the current state of your system ('up to date' or 'updates available'). When clicked, it launches `arch-update` in a terminal window via the [arch-update.desktop](https://github.com/Antiz96/arch-update/blob/main/res/desktop/arch-update.desktop) file.
The systray applet menu shows further information (like the list of pending updates, time of the last and next checks, ...) and allows to trigger specific actions (like running Cachy-Update, check for updates, ...). See [screenshots](#screenshots) for more details.

**Notes:**

- If clicking the systray applet does nothing, please read [this chapter](#run-arch-update-in-a-specific-terminal-emulator).
- GNOME shell does not support systray icons natively, GNOME users need to install the ["AppIndicator and KStatusNotifierItem Support" extension](https://extensions.gnome.org/extension/615/appindicator-support/) for the systray applet to work.

### The automated update checks

To enable automated and periodic checks for available updates, run the following command:

```bash
cachy-update --check --enable
```

By default, a check is performed **at boot and then once a day**. The check cycle can be customized, see [this chapter](#modify-the-check-cycle).

### Screenshots

Once started, the systray applet appears in the systray area of your panel.
It is the first icon on the left in the screenshot below (note that there are [different color variants available](https://github.com/Antiz96/arch-update/blob/main/res/icons/README.md) for it):

![icon](https://github.com/user-attachments/assets/ec5f4ab7-7eb0-4c41-8b2b-9983e789d516)

With [the automated update checks](#the-automated-update-checks) enabled, checks for updates are automatically and periodically performed, but you can manually trigger one from the systray applet icon by right-clicking it and then clicking on the `Check for updates` menu entry. You can also see timestamps report for the last and next update checks:

![check_for_updates](https://github.com/user-attachments/assets/4b73946d-f9f5-4be6-87b8-42112fca642d)

If there are new available updates, the systray icon shows a red circle and a desktop notification indicating the number of available updates is sent. You can directly run Cachy-Update from it or close / dismiss it thanks to the related click actions:

![notif](https://github.com/user-attachments/assets/d96b1831-fc11-4343-9f81-eee2a906961b)

You can see the list of available updates from the menu by right-clicking the systray icon.
A dropdown menu displaying the number and the list of pending updates is dynamically created for each sources that have some (Packages, AUR, Flatpak).
A "All" dropdown menu gathering the number and the list of pending updates for all sources is dynamically created if at least 2 different sources have pending updates:

*Clicking on the entry for a package opens the upstream project's URL in your web browser (except for Flatpak packages).*

![all](https://github.com/user-attachments/assets/f1a6a6de-ac06-4234-a0a8-e5dd326bb5a0)

![packages](https://github.com/user-attachments/assets/f94dfe9f-95b1-46fc-a5fe-fbc8adc704ad)

![aur](https://github.com/user-attachments/assets/cf9cd829-fc97-4a05-9a6a-f5cba1649e29)

When the systray icon is left-clicked, `arch-update` is run in a terminal window (alternatively, you can click the "*X* update(s) available" entry or the dedicated "Run Cachy-Update" one from the right-click menu):

![run](https://github.com/user-attachments/assets/874e4f9e-4498-41bf-b257-1e5ecb782377)

If at least one Arch Linux news has been published since the last run, `Cachy-Update` will offer you to read the latest Arch Linux news directly from the terminal window.
The news published since the last run are tagged as `[NEW]`:

![news](https://github.com/user-attachments/assets/42472294-ce87-4d86-87fc-3adb0f6f3e9e)

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
