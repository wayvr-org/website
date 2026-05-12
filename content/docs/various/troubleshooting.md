---
title: "Troubleshooting"
bookIcon: "troubleshoot"
---

# Troubleshooting

## Check logs

WayVR will often show troubleshooting tips in the logs, so it's good to always check them first.

By default, WayVR logs into `/tmp/wayvr.log`.

Another way is to run WayVR in the terminal with `--replace`. This will stop the WayVR process started by SteamVR/WiVRn and start a new one that can be monitored in the terminal.

---

## Troubleshooting application compatibility issues

- #### My Wayland application doesn't launch but others do!

Even though some applications support Wayland, some still check for the `DISPLAY` environment variable and an available X11 server, throwing an error. This can also be fixed by running [cage](https://github.com/cage-kiosk/cage) on top of them.

- #### My web browser launches inside my desktop instead of WayVR!

Close your web browser on your desktop first, then try again.

---

## Troubleshooting segmentation faults (SIGSEGV)

Run WayVR in `rust-gdb` (or even regular `gdb`) to get more info about the segfault.

Attach this with the other logs that you have.

```
rust-gdb -ex run target/debug/wayvr
```

## Running with environment variables

If you need to provide full debug logs for a bug report, that involves running WayVR with extra environment variables. How to do this depends on how you've obtained WayVR, and how you're launching it.

First, temporarily disable WayVR in the WiVRn dashboard autostart section, Envision plugins menu, or SteamVR startup overlay apps list.

Next, note down the location of your WayVR binary. Below are a few possible locations, based on your [installation method][installation]:

- **Example 1.** You saved the WayVR AppImage to your Documents folder.
  - &rarr; `~/Documents/WayVR-v00.0.0-x86_64.AppImage`
  - Make sure to change the exact filename to match your own copy.
- **Example 2.** You installed the WayVR AppImage with Gear Lever.
  - &rarr; `~/AppImages/wayvr.appimage`
- **Example 3.** You installed WayVR as a [system package][installation], such as on Arch Linux/CachyOS from the AUR, or on NixOS from nixpkgs-xr.
  - &rarr; `wayvr`

Run this command in a new terminal window, replacing `<the wayvr binary>` accordingly:

```shell
RUST_BACKTRACE=full RUST_LOG=debug VK_INSTANCE_LAYERS=VK_LAYER_KHRONOS_validation <the wayvr binary>
```

After reproducing the bug or issue, ensure WayVR is closed. The log file at `/tmp/wayvr.log` should be much larger.

[installation]: /docs/basics/installation
