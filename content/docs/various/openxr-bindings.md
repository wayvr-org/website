---
title: "OpenXR Bindings"
bookIcon: "controller"
---

# OpenXR Bindings

OpenXR Bindings can be configured using a file.

By default, the file does not exist and internal defaults will be used.

Place [openxr_actions.json5](https://github.com/wlx-team/wayvr/blob/main/wayvr/src/backend/openxr/openxr_actions.json5) in `~/.config/wayvr/` and edit it to your liking. **Do not put it in conf.d!**

```bash
wget -O ~/.config/wayvr/openxr_actions.json5 https://raw.githubusercontent.com/wlx-team/wayvr/refs/heads/main/wayvr/src/backend/openxr/openxr_actions.json5
```

To see what bindings are available for each controller type, search for the profile in [the OpenXR specification](https://registry.khronos.org/OpenXR/specs/1.1/html/xrspec.html).
