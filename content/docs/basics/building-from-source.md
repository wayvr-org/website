---
title: "Building from source"
bookIcon: "terminal"
---

# Building from source

If you don't have any special needs and your distribution is supported, [grab the pre-build package here](../installation).

WayVR can be built thicker or thinner, depending on your needs. WayVR makes use of Cargo features to allow you to tailor the build to your system. By default, everything is included.

Help extend this wiki by providing packages for additional distros!

## Base dependencies

The following packages are required:

- Arch: `base-devel cmake libxkbcommon fontconfig dbus alsa-lib python3 wayland`
- Fedora: `cmake libxkbcommon libxkbcommon-devel fontconfig fontconfig-devel dbus dbus-devel alsa-lib alsa-lib-devel libshaderc-devel openssl-devel python3 wayland-devel`
- Ubuntu: `build-essential pkg-config cmake libstdc++-12-dev libxkbcommon-dev fontconfig libfontconfig-dev libdbus-1-dev libasound2-dev python3 libwayland-dev`

## Available features

### Feature `openvr`

Enable this if you plan on using SteamVR

Warning: building without the dependencies will succeed, but the binary won't execute due to `libopenvr_api.so: cannot open shared object file`. In this case, install the dependencies correctly and re-build.

Dependencies:

- Arch: `openvr`
- Fedora: `openvr-devel`
- Ubuntu: `libopenvr-dev libopenvr-api1`

### Feature `openxr`

Enable this if you plan on using Monado or WiVRn

Dependencies:

- Arch: `openxr`
- Fedora: `openxr-devel`
- Ubuntu: `libopenxr-dev`

### Feature `wayland`

Enable this if you're on a Wayland desktop

Dependencies:

- Feature `pipewire` (see below)

### Feature `x11`

Enable this if you're on X11

Dependencies:

- Arch: `libx11 libxext libxrandr`
- Fedora: `libXrandr-devel libXext-devel libX11-devel`
- Ubuntu: `libx11-6 libxext6 libxrandr2 libx11-dev libxext-dev libxrandr-dev libxkbcommon-x11-dev`

### Feature `pipewire`

Add PipeWire capture support. Works on Wayland, as well as X11 with picom only.

Dependencies:

- Arch: `libpipewire clang`
- Fedora: `pipewire-devel clang`
- Ubuntu: `libpipewire-0.3-0 libpipewire-0.3-dev libspa-0.2-dev clang`

### Feature `osc`

Enable this if you want XSO-compatible OSC parameters in VRChat

Supported parameters are explained here: [OSC Parameters](/docs/various/integrations/osc-parameters)

Dependencies: None

# Execute the build

Here are some examples you can do:

```bash
# Build with all features
cargo build --release

# Build for X11+SteamVR
cargo build --release --no-default-features --features=x11,openvr

# Build for Wayland+Monado
cargo build --release --no-default-features --features=wayland,openxr
```

A single executable will be placed at `../target/release/wayvr`.
