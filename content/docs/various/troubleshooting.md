---
title: "Troubleshooting"
bookIcon: "troubleshoot"
---

# Troubleshooting

## Check logs

WayVR will often show troubleshooting tips in the logs, so it's good to always check them first.

By default, WayVR logs into `/tmp/wayvr.log`.

Another way is to run WayVR in the terminal with `--replace`. This will stop the WayVR process started by SteamVR/WiVRn and start a new one that can be monitored in the terminal.

## Troubleshooting segmentation faults (SIGSEGV)

Run WayVR in `rust-gdb` (or even regular `gdb`) to get more info about the segfault.

Attach this with the other logs that you have.

```
rust-gdb -ex run target/debug/wayvr
```
