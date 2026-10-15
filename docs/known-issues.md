# Known issues

Current as of **1.2.0**. Fixed entries stay on this page with the version
that fixed them, so that a search that lands here still confirms the symptom.

Anything not listed here is either on a page of its own (below), in
[Troubleshooting](troubleshooting.md), or has not been seen yet —
[tell us](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose).

## Open

### HDR is unavailable on some Intel-only PCs

On some machines the Intel H.265 encoder accepts frames and never produces any.
PrismDesk detects the stall, falls back to **H.264** and tells the device, so
you get a picture rather than a black screen — but **HDR10 needs H.265**, so on
those machines HDR is not available.

There is no workaround inside PrismDesk. If the PC also has an NVIDIA GPU,
NVENC is used and the problem does not arise.

<!-- FINDINGS_HDR_WINDOWED_VIDEO_OVERSATURATED -->
### Video in a small window looks oversaturated during HDR streaming

While streaming in HDR, a video playing in a small browser window can come out
with colours far too strong. Full-screen video looks right. Once it happens,
pausing does not bring the colours back. The colours are already wrong on the PC
before PrismDesk captures the screen, so it is not something the stream
adds, and where it comes from is not established yet.

Workarounds: watch the video full screen or in a large window, or stream in SDR.

### A second device occasionally fails to get its own screen

Creating a second extended display has been seen to fail with `0xD000000D` from
Windows' indirect display stack. **It did not reproduce in the four-device
test**, and the cause is not established. If you hit it, disconnect and connect
again; and please open an issue with the diagnostics, because it is a case we
have not been able to reproduce.

### A VPN can stop the device from finding the PC

A VPN running on either end can swallow discovery, over Wi-Fi and over USB
tethering alike. We hit this during development: with the VPN up, nothing was
found; with it down, the host appeared immediately.

Discovery is not the only way in: paste the host's connection string into
**Enter a host directly** in the app. If the host is found but connecting still
fails, the VPN is probably sending local traffic into the tunnel — let it leave
your local network alone (often called *exclude private IPs* or *allow LAN
access*), exclude the PrismDesk app from it, or turn it off. Details in
[Troubleshooting](troubleshooting.md#a-vpn-is-on).

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

### The webcam picture pauses briefly when the zoom changes lens

On a device with more than one rear camera, moving the zoom across the point
where it switches lens (on a Pixel 6, between the ultra-wide lens and 1x) holds
the picture the PC receives for about a tenth of a second. That is the device
changing cameras. It has been measured only on a Pixel 6; where the switch
happens differs from device to device.

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
| **Long-run stability** | No soak test has been run, so nothing is claimed about how long a session stays up. |
| **HDR versus SDR cost** | The GPU difference between HDR and SDR, and the bandwidth difference on moving content, have not been measured. |
| **Budget hardware** | One low-cost tablet has been tried, for the basics only; nothing was measured on it. See [Devices](devices.md). |

## Fixed

Nothing listed on this page has been fixed yet. What each release fixed is in
the [Changelog](../CHANGELOG.md).

See also: [FAQ](faq.md) · [Report a bug](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose)
