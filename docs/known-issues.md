# Known issues

Current as of **1.0.0**. Fixed entries stay on this page with the version
that fixed them, so that a search that lands here still confirms the symptom.

Anything not listed here is either on a page of its own (below) or has not been
seen yet — [tell us](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose).

## Open

### HDR is unavailable on some Intel-only PCs

On some machines the Intel H.265 encoder accepts frames and never produces any.
PrismDesk detects the stall, falls back to **H.264** and tells the device, so
you get a picture rather than a black screen — but **HDR10 needs H.265**, so on
those machines HDR is not available.

There is no workaround inside PrismDesk. If the PC also has an NVIDIA GPU,
NVENC is used and the problem does not arise.

### A second device occasionally fails to get its own screen

Creating a second extended display has been seen to fail with `0xD000000D` from
Windows' indirect display stack. **It did not reproduce in the four-device
test**, and the cause is not established. If you hit it, disconnect and connect
again; and please open an issue with the diagnostics, because it is a case we
have not been able to reproduce.

### A VPN can stop the device from finding the PC

A VPN running on either end can swallow discovery, over Wi-Fi and over USB
tethering alike. We hit this during development: with the VPN up, nothing was
found; with it down, the host appeared immediately. Turning the VPN off is the
only workaround.

### USB tethering can drop a laptop's Wi-Fi

On a laptop connected by Wi-Fi, turning on USB tethering can drop the Wi-Fi
connection. If the laptop needs Wi-Fi for something else, you have to choose.
See [Set up over USB](setup-usb.md).

### Drawing apps that use WinTab see no pen

Not a fault, but it is the most common surprise: an app set to **WinTab** sees no
pen at all. Switch it to **Windows Ink**. Details and the exact Krita setting are
in [Pen](pen.md).

### HDR on a panel that cannot use it looks like nothing happened

Some panels report HDR support but cannot go brighter than SDR. HDR10 is sent
and decoded, and the picture looks the same. The app warns before you connect —
see [HDR](hdr.md).

## Not PrismDesk, but it happens while using it

Both are covered on the [Webcam](webcam.md) page:

- **Photos will not save** from the Windows Camera app
  (`0xA00F424F` / `0x80270200`) — a broken Windows library definition, and it
  reproduces with no camera at all.
- **The rear camera looks mirrored in Discord** — Discord mirrors your own
  self-view. What the other side receives is the right way round.

Also on that page: **a camera app can stop responding if the host is stopped or
started while the app holds the camera.** Close the camera app first.

## Not broken, but often asked about

- **No frame rate is advertised.** The rate follows what Windows composes: with a
  75 Hz primary display the achievable rates are 75, 37.5 and 25 — 60 is not on
  that list. See the [FAQ](faq.md).
- **Windows 10 is not supported** and the installer stops on it, by design.
- **The installer triggers a SmartScreen warning.** See
  [SmartScreen](smartscreen.md).

## Measured gaps

Not problems we know about — things we have deliberately not claimed, because
nobody has measured them:

| | |
|---|---|
| **End-to-end latency** | Not published. There is no measurement we would stand behind. If you have a method, say so in [Discussions](https://github.com/Asynchronous-0x4C/prismdesk-app/discussions). |
| **Long-run stability** | No soak test has been run. One two-and-a-half-hour session went fine, and that is an observation, not a test. |
| **HDR versus SDR cost** | The bandwidth and GPU difference between HDR and SDR has not been measured. |
| **Budget hardware** | Nothing in the low-cost bracket has been tried. See [Devices](devices.md). |

## Fixed

Nothing yet — 1.0.0 is the first release.

See also: [FAQ](faq.md) · [Report a bug](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose)
