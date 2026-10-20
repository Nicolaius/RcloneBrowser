# Customizations in this fork

This fork of [Alkl58/RcloneBrowser](https://github.com/Alkl58/RcloneBrowser)
(itself derived from [kapitainsky/RcloneBrowser](https://github.com/kapitainsky/RcloneBrowser)
and the original work by Martins Mozeiko) adds a few interface options.
The original license (MIT) and copyright notices are unchanged.
Part of the code was written with the help of an AI assistant (Claude) and
reviewed and tested by the maintainer of this fork.

## New features

- **Remotes icon size as a multiplier** – Preferences → GUI style → Remotes icon
  size: the XS/S/M/L/XL radio buttons are replaced by a numeric field
  (`0.5` – `20.0`, default `4.0`). Both `.` and `,` are accepted as decimal
  separator. Old letter values stored in the config are converted automatically.
- **Remotes in `rclone listremotes` order** – the list of remotes is no longer
  sorted case-insensitively; uppercase names come before lowercase ones.
- **Tighter rows in list (long) mode.**
- **Hide Tasks / Queue / Scheduler tabs** – Preferences → Interface → Tabs, three
  checkboxes on one row.
- **Colored text for the fixed tabs** (Remotes, Jobs, Tasks, Queue, Scheduler) –
  change `FIXED_TABS_TEXT_COLOR` (`#rrggbb`) at the top of `src/main_window.cpp`.
- **Hide remote icons** – Preferences → Interface → User Interface → "Hide remote
  icons": hides the row of icons inside opened remote tabs. The icons of the fixed
  tabs are never affected. All actions remain available from the right-click menu.
  Applies immediately to already opened tabs.
- **Player chooser for streaming** – in Preferences → Stream command you can list
  several players separated by `|`, e.g.

  ```
  mpv - | vlc - | mplayer - | audacious -
  ```

  When streaming a file a small dialog asks which player to use. With a single
  command nothing changes. Arguments and `$file_name` work as before.

## Settings keys added (`rclone-browser.conf`, section `[Settings]`)

| key | meaning |
|---|---|
| `iconSize` | now a number (multiplier) |
| `hideTasksTab`, `hideQueueTab`, `hideSchedulerTab` | hide the optional tabs |
| `hideRemoteIcons` | hide the icon row in remote tabs |
| `stream` | may contain several commands separated by `\|` |

## Build

See the build instructions of the original README (Qt6, CMake):

```
mkdir build && cd build
cmake ..
make -j$(nproc)
```
