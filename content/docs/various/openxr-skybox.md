---
title: "OpenXR Skybox"
bookIcon: "photosphere"
---

# OpenXR Skybox

WayVR comes with a skybox for OpenXR.

# Skybox vs Passthrough

Turning off the skybox and using passthrough or the solid black background allows WiVRn to allocate more of the video stream to your WayVR apps and screens, resulting in a better quality image.

This is specific to WiVRn, there is no change with wired Monado headsets.

# Changing the Skybox

There is a skybox catalog under the Look and Feel tab of Settings.

Also, if you have a nice skybox with a permissive license, contact us and we may be able to add it to the catalog for you!

# Bring your own Skybox

A custom texture may be set by changing the `skybox_texture` in the file `~/.config/wayvr/conf.d/zz-saved-config.json5`.

The path you set is relative to `~/.config/wayvr/`.

Criteria:

- Path can be absolute, or relative to `~/.config/wayvr/`.
- File must be DDS (See: [Custom Textures](/docs/various/custom-textures))
- Image must be an equirectangular (aka "HDRI" or "Spherical 360") image.
