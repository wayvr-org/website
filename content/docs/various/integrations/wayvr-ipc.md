---
title: "WayVR IPC (wayvrctl)"
description: "Control WayVR via CLI with wayvrctl - manage windows, processes, haptics, and GUI elements."
---

# WayVR IPC + Wayvrctl

You can control WayVR directly via its built-in IPC using `wayvrctl`. This CLI tool extends WayVR capabilities by enabling bash scripting for various widget behaviors and process management.

See `wayvrctl --help` for more information.

# Available commands

---

## Batch Processing

```bash
# Reads commands from stdin, one per line
wayvrctl batch --fail-fast
```

---

### Get position of HMD & controllers

```bash
wayvrctl input-state
```

Example output: `{"hmd_pos":[0.0,1.6,0.0],"left":{"pos":[-0.2,1.3,-0.5]},"right":{"pos":[-0.2,1.3,-0.5]}}`

---

### List WayVR windows

```bash
wayvrctl window-list
```

Example output:

```txt
anchor
watch
Dashboard
grab-help
alttab-help
wayvr/app/3:vlc
wayvr/session/36:e20f2343-51d4-4549-9ef8-27fe77a51459/Dolphin#1
```

### Change the visibility of a window on a WayVR display

```bash
wayvrctl window-set-visible <name> <visible_0_or_1>
```

Example: `wayvrctl window-set-visible Dashboard 1`

### Get/set window state

Possible values:

- `alpha`: Overlay opacity (0.1 to 1.0)
- `additive`: Use additive blending when alpha < 1.0
- `grabbable`: Whether this overlay reacts to grab action
- `interactable`: Whether laser pointers hit or pass through this overlay
- `positioning`: Overlay positioning: floating, anchored, static, follow_head, follow_hand_left, follow_hand_right
- `curvature`: Screen curvature, 0 is disabled
- `block_input`: Whether hovering this overlay will block inputs to other VR apps
- `align_to_hmd`: Whether the overlay billboards towards the HMD
- `global`: Whether the overlay is shown on all sets (unaffected by set switching)

_(The list might be incomplete, run `wayvrctl window-state help get` for more information)_

Example #1: `wayvrctl window-state Dashboard get alpha`

Example #2: `wayvrctl window-state Dashboard set alpha 0.5`

### Get/set window attrib

Possible values:

- stereo: Stereo mode: none, left_right, right_left, top_bottom, bottom_top
- stereo_full_frame: Whether stereo content is rendered in full frame
- stereo_adjust_mouse: Whether the mouse position is adjusted for stereo
- mouse_transform: Mouse transform: default, normal, rotated90, rotated180, rotated270, flipped, flipped90, flipped180, flipped270
- window_size: Window size in pixels, for example: 1920x1080

(The list might be incomplete, run `wayvrctl window-attrib help get` for more information)

Example #1: `wayvrctl window-attrib wayvr/app/3:vlc get window_size`

Example output: `[1920, 1080]`

Example #2: `wayvrctl window-attrib wayvr/app/3:vlc set window_size 1280x720`

---

### List all processes managed by WayVR

```bash
wayvrctl process-list
```

Example output: `[{"name":"eglgears_wayland","handle":12345,"userdata":{}}]`

### Get WayVR-managed process info

```bash
wayvrctl process-get <handle>
```

Example: `wayvrctl process-get 4294967298`

Example output:

```json
{
	"handle": 4294967298,
	"name": "vlc",
	"userdata": {
		"desktop-entry": "{\"exec_argv\":[\"/usr/bin/vlc\",\"--started-from-file\"],\"app_id\":\"vlc\",\"app_name\":\"VLC media player\",\"icon_path\":\"/usr/share/icons/hicolor/128x128/apps/vlc.png\",\"categories\":[\"AudioVideo\",\"Player\",\"Recorder\"]}"
	}
}
```

### Terminate a WayVR-managed process

```bash
wayvrctl process-terminate <handle>
```

`handle`: A process handle (number) returned by `process-list`, `process-get` or `process-launch`

### Launch a new process inside WayVR

Reach out `wayvrctl help process-launch` for detailed information:

```
Usage: wayvrctl process-launch [OPTIONS] <COMMAND>...

Arguments:
  <COMMAND>...  Executable and optional arguments

Options:
  -n, --name <NAME>              Name for the overlay [default: ""]
  -e, --env <ENV>                Environment variables, separated by comma [default: ""]
  -r, --resolution <RESOLUTION>  [default: 1920x1080]
  -p, --pos <POS>                Default positioning [default: anchored] [possible values: floating, anchored, static]
  -i, --icon <ICON>              Absolute path to the app icon [default: ""]
  -h, --help                     Print help
```

Example #2: `wayvrctl process-launch dolphin --resolution 512x512 --pos floating`

Example output: `4294967299` (returns process handle)

---

### GUI widget modifications

Reach out `wayvrctl panel-modify --help` for detailed information:

```
Usage: wayvrctl panel-modify <OVERLAY> <ELEMENT> <COMMAND>

Commands:
  set-text          Set the text of a <label> or <Button>
  set-color         Set the color of a <rectangle> or <label> or monochrome <sprite>
  set-image         Set the content of a <sprite> or <image>. Max size for <sprite> is 256x256
  set-visible       Set the visibility of a <div>, <rectangle>, <label>, <sprite> or <image>
  set-sticky-state  Set the sticky state of a <Button>. Intended for buttons without `sticky="1"`
  help              Print this message or the help of the given subcommand(s)

Arguments:
  <OVERLAY>  The name of the overlay (XML file name without extension)
  <ELEMENT>  The id of the element to modify, as set in the XML
```

---

### Trigger haptics on the user's controller

`wayvrctl haptics [OPTIONS] <DEVICE>`

```
Options:
  -i, --intensity <INTENSITY>  [default: 0.25]
  -d, --duration <DURATION>    [default: 0.1]
  -f, --frequency <FREQUENCY>  [default: 0.1]
  -h, --help                   Print help
```

`device`: 0 for left, 1 for right controller (default: 0)

Example: `wayvrctl haptics --intensity 0.42 --duration 0.5 --frequency 0.1 0`

---

### Toggle overlay show/hide state (show/hide your keyboard and displays)

```bash
wayvrctl show-hide
```

### Switch set

```bash
wayvrctl switch-set <set_or_0>
```

Set number to switch to, 0 to hide all sets

`set_or_0`: Number to switch to (0 hides all sets)
