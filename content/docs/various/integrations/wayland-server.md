---
title: "WayVR's Wayland Server"
---

# Wayland Server

Internally, WayVR uses [Smithay](https://github.com/Smithay/smithay) compositor.

### Launching external apps inside WayVR

To launch your app externally:

```sh
DISPLAY= WAYLAND_DISPLAY=wayland-$(cat $XDG_RUNTIME_DIR/wayvr.disp) yourapp
```

or (in the most cases):

```
DISPLAY= WAYLAND_DISPLAY=wayland-20 yourapp
```

Setting `DISPLAY` to an empty string forces various apps to use Wayland instead of X11.

# Troubleshooting
