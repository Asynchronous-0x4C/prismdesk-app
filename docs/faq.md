# FAQ

Questions people actually asked. New ones get added here rather than invented.

### Is it open source?

No. This repository holds the documentation, the issue tracker and the releases;
the product itself is closed source.

### Does it work over the internet, or from a café?

No. The PC and the device have to be on the same local network — over Wi-Fi, over
Ethernet, or over [USB tethering](setup-usb.md). PrismDesk is a second monitor,
not remote desktop, and it is not a way to reach your desktop from somewhere
else.

### Does it work on Windows 10?

No. **Windows 11 64-bit, build 22000 or later.** The installer stops on anything
older rather than installing something that half works. Windows 10 has not been
tested, so it is not claimed.

### Does it work with an iPad, or on macOS or Linux?

No. Windows 11 on the PC side, Android 8.0 or later on the device side.

### What frame rate do I get?

We do not advertise one, and we would rather explain why than pick a number.

The rate follows what Windows composes for the virtual display. With a 75 Hz
primary display, the achievable rates are 75, 37.5 and 25 — **60 is simply not on
that list.** On a 60 Hz machine the list is different again. Anyone promising you
a frame rate is promising you the number from their monitor, not yours.

### How fast is it? What is the latency?

**We do not publish a latency figure, because we have not measured one we would
stand behind.** Measuring end to end honestly is harder than it sounds, and a
number taken from the app's own reporting would be marking our own homework.

If you know how you would measure it, we would like to hear it —
[Discussions](https://github.com/Asynchronous-0x4C/prismdesk-app/discussions).

### Do I need a licence for every PC?

No. **One key covers three of your own Windows PCs.** PrismDesk is
US$22 — One-time purchase. No subscription, no account. The free edition covers the basics — one device, SDR, pen and touch input, and audio. Pro adds HDR, up to four devices at once, and your device camera as a Windows webcam. Pro is sold by Polar Software,
Inc. as merchant of record. If it does not work on a PC that meets the
requirements and we cannot fix it with you, there is a refund within 14 days:
[https://prismdesk.app/refund](https://prismdesk.app/refund).

### Does it send anything to you?

**No usage data, ever.** No account, no telemetry, and **no automatic update
check**. The pixels go straight from your PC to your device.

**PrismDesk reaches the internet only while you are pressing one of two kinds of
button**, and never in the background or at start-up:

- **Check for updates** (Settings tab) fetches one small file from our website
  that says which version is the latest. **No version number, nothing about your
  PC, and no identifier of any kind is sent** — we cannot tell one press from
  another. Nothing is downloaded or installed; if there is a newer version,
  PrismDesk says so and offers to open the download page.
- The three licence buttons below.

**Press neither, and the app never leaves your own network.**

**PrismDesk Pro contacts our payment provider, Polar, only when you press
Activate, Check licence or Deactivate this PC** — never in the background and
never at start-up. What is sent is the licence key you typed in and a name for
this PC that the app shows you first. After that, Pro needs no connection,
and it keeps working even when Polar is unreachable. See
[https://prismdesk.app/privacy](https://prismdesk.app/privacy).

### Is my screen encrypted on the wire?

Yes. **TLS 1.3** on the control and input channels; **AES-256-GCM** on video,
audio and camera. The device pins the PC's certificate fingerprint, which is why
connecting by QR code or connection URI is better than typing an address — those
two carry the fingerprint, and a typed address does not.

### Why does it want administrator rights?

Creating the virtual display requires them: the display node belongs to the
process that made it, and Windows only lets an elevated process make one. The
start-up entry the installer creates runs it elevated at sign-in, so you are not
asked every time.

### My drawing app ignores the pen

It is almost certainly set to WinTab. Switch it to **Windows Ink** — see
[Pen](pen.md).

### Do I have to turn HDR on?

No. Both ends check what they can do and pick HDR when it would actually look
different. The **Color space** setting says which answer your device will get
before you connect, and you can still choose SDR or HDR10 by hand.
See [HDR](hdr.md).

### I chose HDR10 and nothing changed

Most often the panel reports HDR support but cannot actually go brighter than
SDR; the app says so where you choose it. That is also why the automatic answer
on such a panel is SDR. See [HDR](hdr.md).

### Can I use more than one device at once?

Yes, up to four, sharing one capture and one encoder. Four is the number that was
verified — see [Devices](devices.md).

### Does sound come across?

Yes, the PC's audio can play on the device. It is chosen before connecting and
cannot be switched mid-session.

### What happens when I uninstall?

The driver, the firewall rules, the start-up entry and the virtual camera
registration all go, and settings and diagnostic logs are deleted by default —
the uninstaller offers to keep them if you would rather.

See also: [Known issues](known-issues.md) · [Devices](devices.md) ·
[Discussions](https://github.com/Asynchronous-0x4C/prismdesk-app/discussions)
