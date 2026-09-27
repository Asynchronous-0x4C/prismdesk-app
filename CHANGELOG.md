# Changelog

What changed in each release, written for the people who use PrismDesk.

The version number is the one in the host window's title bar, and on the device
under Settings → About → Third-party licenses.

## 1.0.0 — not released yet

The first release. Everything below is new because there is nothing before it.

### Added

- **A real second monitor over Wi-Fi.** PrismDesk installs a virtual display
  driver, so Windows sees an extra monitor with its own resolution and refresh
  rate — not a mirrored window.
- **HDR10**, end to end, on devices and panels that can actually show it.
  [What has to be true on both ends](docs/hdr.md).
- **Pen with pressure, tilt and rotation**, delivered as real Windows pen input.
  [Pen](docs/pen.md).
- **Up to four devices at once**, sharing one capture and one encoder.
- **The device camera as a Windows webcam**, listed as "PrismDesk Camera".
  [Webcam](docs/webcam.md).
- **Audio from the PC**, played on the device.
- **Encryption on by default.** TLS 1.3 on control and input, AES-256-GCM on
  video, audio and camera. The device pins the PC's certificate fingerprint.
- **Nothing to configure after installing.** The installer adds the display
  driver, the firewall rules and the start-up entry. Sign in to Windows and the
  PC is listening.
- **Finding the PC.** The app discovers it on the network, or you scan the QR
  code the host shows, or you type the address.
- **USB.** Works over USB tethering when you would rather not use Wi-Fi, and
  without turning on USB debugging. [Set up over USB](docs/setup-usb.md).
- **Recovery from a short outage.** Cutting Wi-Fi for a few seconds resumes the
  same session instead of ending it.
- **Numbers you can check.** A stats panel on the device and a diagnostics
  export on the PC, so a bug report can carry evidence.
- **English and Japanese**, on both ends.

### Known issues

Current problems and their workarounds are in
[docs/known-issues.md](docs/known-issues.md). The limits that are not bugs, and
the numbers that have not been measured, are in the README.
