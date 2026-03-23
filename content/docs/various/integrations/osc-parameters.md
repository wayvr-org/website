---
title: "OSC Parameters"
---

# OSC (Open Sound Control) parameters

For compatibility, WayVR implements all of the OSC parameters from [XSOverlay](https://xsoverlay.vercel.app/OSC) and most from [OVR Toolkit](https://wiki.ovrtoolkit.co.uk/#/OSC), as well as several more for extended functionality.

This requires WayVR to be built with the `osc` feature, which is enabled by default.

# Configuration

The port used by WayVR can be configured with the `osc_out_port` config value:

```yaml
# ~/.config/wayvr/conf.d/osc_out_port.yaml

osc_out_port: 9000
```

# VRChat Parameters

All of the following parameters are prefixed with `/avatar/parameters/` for use with VRChat; keep this in mind when using these parameters for other programs.

## Overlay Parameters

- `isOverlayOpen` or `ToggleWindows` (bool): True if any overlay window is shown.
- `isKeyboardOpen` or `ToggleKeyboard` (bool): True if the keyboard is shown.
- `isWristVisible` (bool): True if the watch overlay is visible.
- `openOverlayCount` (int >= 0): The amount of open overlay windows in the current working set.
- `isEditModeActive` or `ToggleEditMode` (bool) - Whether "Working Set Edit Mode" is currently active.
- `currentWorkingSet` or `CurrentProfile` (int >= 0) - The currently active working set, 0-indexed. (todo: check if this is 1 or 0-indexed in OVR Toolkit)
- `totalWorkingSets` (int >= 0) - The total amount of working sets that have been created.

## Headset Parameters

- `hmdBattery` (float 0-1): The battery level of the headset.
- `hmdCharging` (bool): True when the headset is charging.

## Controller Parameters

- `leftControllerBattery` `rightControllerBattery` (float 0-1): The battery level of the controller.
- `leftControllerCharging` `rightControllerCharging` (bool): True when the controller is charging.
- `averageControllerBattery` (float 0-1): Average battery level of controllers.

## Tracker Parameters

Tracker parameters dynamically increase in number for as many tracker devices exist. For example, with 3 trackers WayVR will send parameters for `tracker1`, `tracker2`, and `tracker3`.

- `tracker<id>Battery` or `tracker1Battery`, etc (float 0-1): 1-indexed tracker device battery level.
- `tracker<id>Charging` or `tracker1Charging`, etc (bool): 1-indexed tracker device charging state.
- `averageTrackerBattery` (float 0-1): Average battery level of all trackers.
- `lowestBattery` or `LowestBattery` (float 0-1): The lowest battery level out of all devices, including the HMD, controllers, and trackers.

## Excluded Parameters

The following parameters are currently missing for full parity:

### OVR Toolkit

- `MediaPlaying` (bool) - Whether the overlay is currently playing media.
  - WayVR does not directly support controlling media playback, however it should be possible to create a button which sends this parameter as an `::OscSend` Button Action alongside a command to play or pause media.
