---
title: "OpenXR Skybox"
bookIcon: "photosphere"
---

# OpenXR Skybox

WayVR comes with a skybox for OpenXR.

# Turning off Pass-through

Some headsets will show a camera pass-through by default. If skybox is preferred, go to settings, uncheck `Use passthrough`, then scroll down and `Restart software`.

# Changing the Skybox

We are only allowed to include pieces with specific licenses in the git repo, but feel free to procure your own skybox materiel for personal use!

A custom texture may be set via `~/.config/wayvr/conf.d`:

```bash
echo 'skybox_texture: my-skybox.dds' > ~/.config/wayvr/conf.d/skybox.yaml
```

Criteria:

- Path can be absolute, or relative to `~/.config/wayvr/`.
- File must be DDS (See: [Custom Textures](/docs/various/custom-textures))
- Image must be an equirectangular (aka "HDRI" or "Spherical 360") image.
