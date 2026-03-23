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
