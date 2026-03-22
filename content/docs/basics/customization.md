---
title: "UI Customization"
bookIcon: "magic_button"
---

# WayVR UI Customization

## Dashboard settings

The settings panel has many of the settings already. Only use settings files for settings that are not present in the dashboard.

## Custom colors

Changing the colors of WayVR can be done via the configs.

Create `~/.config/wayvr/conf.d/theme.yaml` as such:

```yaml
color_accent: "#008cff"
color_danger: "#ff3300"
color_faded: "#668299"
```

## Custom timezones

Create `~/.config/wayvr/conf.d/clock.yaml` as such:

```yaml
timezones:
  - "Europe/Oslo"
  - "America/New_York"
```

Once this file is created, the various settings in custom UI that accept the `_timezone` property will use these custom alternate timezones (instead of the default set, which are selected as major ones on different continents from your current actual timezone).

The first timezone is selected with `_timezone="0"`, the second with `_timezone="1"`, and so on.

There is **no need to specify your own local timezone** in here; omitting `_timezone` from a `_source="clock"` Label will display local time.

## Customizing sounds

Audio files with the following names can be added to `~/.config/wayvr/sound/`, and will replace the original sounds:

- `toast.mp3` - Notification Toast appears.
- `key_click.mp3` - Keyboard Key is pressed.
- `wgui_mouse_enter.mp3` - Laser Pointer enters a clickable element.
- `wgui_button_press.mp3` - Button Element is pressed.
- `wgui_button_release.mp3` - Button Element is released.
- `wgui_checkbox_check.mp3` - Checkbox Element is checked.
- `wgui_checkbox_uncheck.mp3` - Checkbox Element is unchecked.
- `startup.mp3` - Dashboard is created. (i.e. opened for the first time this session)
- `app_start.mp3` - App is launched from the dashboard.

## Customizing keyboard, watch, etc

Place custom XML files under `~/.config/wayvr/theme/gui`

The default XML files can be found in [src/assets/gui](https://github.com/wlx-team/wayvr/tree/main/wayvr/src/assets/gui).

The `uidev` utility is provided for testing UI elements outside of VR:

```sh
cd uidev
TESTBED=../wayvr/src/assets/gui/watch.xml cargo run
```

## Adding custom overlay panels

Place the XML file and assets for your custom panel under `~/.config/wayvr/theme/gui`

Make sure that the name you choose doesn't override an existing, built-in overlay: [src/assets/gui](https://github.com/wlx-team/wayvr/tree/main/wayvr/src/assets/gui)

Add your overlay to the `custom_panels` setting via `conf.d`:

Example for an XML named `my-panel.xml`:

```yaml
# ~/.config/wayvr/conf.d/panels.yaml

custom_panels:
  - "my-panel"
```

Your new panel will show up on the overlay list on the next start.

## WayVRCtl

`wayvrctl` is a CLI tool to interact with WayVR.

Install: `cargo install --git https://github.com/wlx-team/wayvr.git wayvrctl`

For a full list of commands, see: `wayvrctl --help` and `wayvrctl panel-modify --help`.

Examples:

```sh
# Set the text on <label id="mylabel" .. /> from mypanel.xml to "It works!":
wayvrctl panel-modify mypanel mylabel set-text "It works!"

# Change the image of an <image> element:
wayvrctl panel-modify mypanel myimage set-image /tmp/album-art.png

# Adjust multiple elements at the same time (more efficient than multiple calls):
echo '
panel-modify mypanel now_playing_title set-color "#ff0000"
panel-modify mypanel now_playing_artist set-color "#00ff00"
panel-modify mypanel now_playing_album set-color "#0000ff"
' | wayvrctl batch
```

## Basic UI Elements (Wgui)

The available widgets and their attributes are documented at: [wgui/doc/widgets.md](https://github.com/wlx-team/wayvr/blob/main/wgui/doc/widgets.md)

## Custom UI Elements (WayVR)

An up-to-date list of custom functions, see [wayvr/src/gui/README.md](https://github.com/wlx-team/wayvr/blob/main/wayvr/src/gui/README.md)
