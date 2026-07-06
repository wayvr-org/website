---
title: "OpenXR Bindings"
bookIcon: "controller"
---

# OpenXR Bindings

Unlike in the case of SteamVR, OpenXR (Monado/WiVRn) bindings are configured in WayVR itself.

Access the Bindings interface from the Dashboard's Controls tab.

Most modern headsets (other than Steam Frame) use the **Touch Controller** schema.

Note that chords are not supported at this time.

# Advanced

See your `~/.config/wayvr/openxr_actions.json5` file. Editing the file manually allows you to make some esoteric binding setups, or even add new controller types.

To see what bindings are available for each controller type, search for the profile in [the OpenXR specification](https://registry.khronos.org/OpenXR/specs/1.1/html/xrspec.html).
