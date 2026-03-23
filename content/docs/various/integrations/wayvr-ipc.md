---
title: "WayVR IPC (wayvrctl)"
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

## Input State

#### Get position of HMD & controllers

```bash
wayvrctl input-state
```

Example output: `{"hmd_pos":[0.0,1.6,0.0],"left":{"pos":[-0.2,1.3,-0.5]},"right":{"pos":[-0.2,1.3,-0.5]}}`

---

## Window Management

#### List WayVR windows

```bash
wayvrctl window-list
```

Example output: `[{"size_x":1920,"size_y":1080,"visible":true,"handle":{"idx":0,"generation":1},"process_handle":{"idx":0,"generation":1}}]`

#### Change the visibility of a window on a WayVR display

```bash
wayvrctl window-set-visible <handle> <visible_0_or_1>
```

`handle`: A JSON window handle returned by window-list

Example: `wayvrctl window-set-visible "{\"idx\":0,\"generation\":1}" 1`

---

## Process Management

#### List all processes managed by WayVR

```bash
wayvrctl process-list
```

Example output: `[{"name":"eglgears_wayland","handle":{"idx":0,"generation":1},"userdata":{}}]`

#### Get WayVR-managed process info

```bash
wayvrctl process-get <handle>
```

`handle`: A JSON process handle returned by `process-list` or `process-launch`

Example: `wayvrctl process-get "{\"idx\":0,\"generation\":1}"`

#### Terminate a WayVR-managed process

```bash
wayvrctl process-terminate <handle>
```

`handle`: A JSON process handle returned by `process-list` or `process-launch`

#### Launch a new process inside WayVR

Reach out `wayvrctl process-launch --help` for detailed information:

```xml
Usage: wayvrctl process-launch [OPTIONS] <EXEC> [RESOLUTION] <POS> [ICON] [ARGS]

Arguments:
  <EXEC>        Executable to run
  [RESOLUTION]  [default: 1920x1080]
  <POS>         Default positioning [possible values: floating, anchored, static]
  [ICON]        Absolute path to the app icon
  [ARGS]        Arguments to pass to executable [default: ]

```

Example: `wayvrctl process-launch eglgears_wayland "1280x720" floating`

Available position modes: `floating`, `anchored`, `static`

Example output: `{"idx":42,"generation":123}`

---

## GUI widget modifications

Reach out `wayvrctl panel-modify --help` for detailed information:

```xml
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

## Haptics

#### Trigger haptics on the user's controller

`device`: 0 for left, 1 for right controller (default: 0)

`intensity`: Haptic intensity (default: 0.25)

`duration`: Haptic duration (default: 0.1)

`frequency`: Haptic frequency (default: 0.1)

```bash
wayvrctl haptics -i <intensity> -d <duration> -f <frequency> <device>
```

Example:

`wayvrctl haptics -i 0.42 -d 0.1 -f 0.1 0`

---

## Overlay Management

#### Toggle overlay show/hide state (show/hide your keyboard and displays)

```bash
wayvrctl show-hide
```

#### Switch set

```bash
wayvrctl switch-set <set_or_0>
```

Set number to switch to, 0 to hide all sets

`set_or_0`: Number to switch to (0 hides all sets)
