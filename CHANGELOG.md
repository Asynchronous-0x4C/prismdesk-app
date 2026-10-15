# Changelog

What changed in each release, written for the people who use PrismDesk.

The version number is the one in the host window's title bar, and on the device
under Settings → About → Third-party licenses.

## 1.2.0 — 2026-10-14

Update both ends: the host on the PC and the app on the device. 1.2.0 does not
connect to 1.0.0 or 1.1.0 in either direction. The 1.2.0 app says that PrismDesk
on the PC is too old, and the 1.2.0 host tells an older app that it must be
updated. Update the PC first, then the app.

### Added

- **Input device mode (Pro).** Choose **Input device (no screen)** under
  **Display mode** in the app's Settings. The device sends no picture and no
  sound, and the PC gets no virtual display. Instead the device becomes a pen
  tablet for a screen the PC already has, with **Ctrl**, **Shift**, **Alt** and
  **Space** keys that stay pressed while touched, **Undo**, **Redo**, **Camera**
  and **End**. The pen area keeps the screen's shape and is redrawn when that
  screen's resolution or orientation changes, and the device turns as set in
  **Orientation while streaming**. In portrait the keys sit in rows below the pen
  area. On the host, such a device shows as **Device I/O** and **No video (input
  only)** in the client list, and the License section lists **Device I/O mode**.
  The mode cannot be changed during a session: disconnect and choose again.
- **Choosing the screen for the pen and touch.** In input device mode, with two
  or more screens on the PC, **Screen** sends the pen and touches to another
  screen. Each new connection starts on the main monitor.
- **Undo and Redo that match the app (Pro).** In input device mode, **Undo** and
  **Redo** send the shortcut of the app in front on the PC at the moment you
  press them. Other apps get Ctrl+Z and Ctrl+Y.
- **Zoom for the device camera (Pro).** While streaming, **Camera** in the
  controls opens a panel with **Send to PC**, **Front** / **Rear**, a zoom slider
  with quick steps, and a preview of what the PC receives. The zoom happens on
  the device, so apps on the PC get the zoomed picture, and going below 1x uses
  the ultra-wide lens on devices that have one. Zoom is remembered separately for
  landscape and portrait. Set the starting zoom under Settings → **Camera (Pro)**
  → **Zoom**. With **Save zoom changed while streaming** off, a change lasts only
  until you turn the camera off or disconnect.
- **Notices in Check for updates.** When we publish a short notice, for example
  about a problem in a released version, **Check for updates** on the host shows
  it under **Notice**, even if you already run the latest version. It is plain
  text, never a link, and the host still contacts us only when you press the
  button.

### Changed

- **Going back to this host from a later version keeps your settings and
  license.** From 1.2.0 on, the host reads the settings and license files that a
  later version wrote, instead of setting them aside and starting from the
  defaults.
- **The host window hides connection details by default.** The PIN, the QR
  code, the fingerprint and the connection string no longer show up in screen
  shares or recordings. Press **Show** to reveal them for 30 seconds; they hide
  again when a device connects. To keep them visible, turn off **Hide connection
  details** on the host's Settings tab.
- **The app's Settings marks Pro features before you connect:** **Camera (Pro)**
  and **HDR10 (Pro)**. They are still greyed out only while connected to a host
  running the free edition.
- **Gestures that start at the right edge now reach the PC.** A vertical drag, a
  long press or a two-finger gesture that began at the right edge used to send
  nothing until you lifted your finger. A swipe to the left still opens the
  controls. If you first hold your finger still at the edge, or the drag goes up
  or down before it goes left, the controls do not open for that gesture.

### Fixed

- **Keys stayed pressed on the PC after a device disconnected or the connection
  dropped.** Only mouse buttons were let go.
- **With several devices connected, a connection that closed before it finished
  could let go of keys and buttons held from another device.**
- **The first start after a new install ran with Pro features on and no
  license**, and so did every start on a PC where the host could not save its
  settings. It now starts as the free edition.
- **Without a license, the License section said "Running as the Free edition
  (developer switch)".** It now says **Free edition**.
- **While mirroring, rearranging the PC's screens could put the mark and "Now:"
  in Screen to show on the wrong screen**, and tapping the screen actually shown
  did nothing.
- **The host window could stay white or grey after starting**, especially when
  it started while the PC's screen was off.
- **The first stream after starting the host could fall back to Desktop
  Duplication**, which does not show the mouse cursor, instead of Windows
  Graphics Capture.
- **After the display driver restarted, every new connection failed until the
  host was restarted.** The host now reconnects to the driver. We have seen the
  driver restart about 5 seconds after the PC's screen turned off. We could not
  make that happen on demand to test the whole path, and what makes the driver
  restart is not fixed.
- **A device that connected just as the host was stopping could leave a virtual
  display behind.**
- **If another program was using the camera port, the host started anyway.** It
  now stops and says **Could not listen on the camera/heartbeat port (another
  program may be using it).**
- **The host could now and then miss a search request, a keep-alive or a camera
  frame that arrived after a quiet moment.**
- **The app could close when you went to the home screen while streaming.** We
  saw it once and could not make it happen again; the fix follows the cause the
  crash pointed to.
- **The QR scanner stopped reading codes after it had seen one that was not from
  PrismDesk.**
- **The camera button did nothing after camera permission was denied for
  good.** The app now says **Camera permission has not been granted.** with
  **Open app settings**.
- **With a finger already on the screen, the pen was sent as touch.**
- **The picture could freeze without an error after a decoding problem.** The
  app now keeps retrying, waiting a little longer each time.
- **The picture could break up after packets were lost or arrived late**: frames
  that depended on a missing one were still shown, and an old frame completed
  late could appear after a newer one.
- **PC audio could stay silent for the rest of the connection** after the
  device's audio output changed and setting it up failed. It now tries again
  after about 2 seconds.
- **The streaming notification could stay after disconnecting.**
- **If the PC's name could not be looked up while connecting, the app stopped
  without a word.** It now goes back to the list.
- **Turning the device back could leave the webcam picture on the PC rotated the
  old way.**
- **A PC reached over USB tethering that was turned on during a search was
  listed as an ordinary network connection.**

### Known issues

New: **the webcam picture pauses briefly when the zoom changes lens.**
See [docs/known-issues.md](docs/known-issues.md).

## 1.1.0 — 2026-10-10

Update both ends: the host on the PC and the app on the device. Either one
still works with the other's 1.0.0, but some of the protections below only
apply once both are 1.1.0.

### Added

- **A pairing PIN by default.** A new install creates a 6-digit PIN, and so does
  updating a PC that had none. Scanning the QR code still needs no typing.
  Picking the PC from the list asks for the PIN once, and the device then
  remembers it for that PC. To go back to no PIN, use **Remove the PIN** under
  "Security" on the host's Settings tab.
- **How sure the device is about the PC.** Saved PCs, the connection and the
  stats panel show **Verified** (confirmed with the QR code), **Encrypted** or
  **Not encrypted**. For a PC that is not verified, the device shows the start of
  its fingerprint so you can compare it with the one on the PC. The PIN and the
  fingerprint are now next to the QR code on the host's Connect tab.
- **A new capture method, Directly from the driver.** The host takes the
  virtual display's picture straight from the display driver instead of
  capturing the screen again. It is the new default (**Directly from the driver
  (recommended, virtual displays only)**). When it cannot be used — for example
  another screen has a higher refresh rate, or the screen is rotated — the host
  uses Windows Graphics Capture and shows the reason under "Capture method".
  The option **Match the virtual display's refresh rate to the fastest screen**
  (off by default) keeps it in use in that case.
- **Choosing a screen while extended.** **Screen to show** on the device now
  works in extend mode too: pick another screen to mirror it, or **This device**
  to go back. Windows stay where they are. Needs the 1.1.0 host.
- **A hint for networks that keep devices apart.** When nothing is found, the
  app suggests the PC's Mobile hotspot, and a PC reached that way is marked
  **Hotspot**.
- **A reminder to update the PC.** After the app is updated, it says once:
  **Update PrismDesk on your PC too.** It does not go online to check.

### Changed

- **Switching profile or mode no longer recreates the virtual display**, so
  windows on it are not thrown back to the main monitor.
- **The mode and profile buttons on the host's Connect tab are gone.** They did
  not show the current setting and changed only the first device without
  telling it. Change mode and profile on the device; the host's client list
  shows each device's current mode and profile.
- **New connections ask for 60 Hz** instead of the device panel's own rate,
  which some PCs could not provide. Choosing a frame rate still sets it.
- **Prefer NVENC** now starts on only on PCs that have an NVIDIA GPU. PCs
  without one no longer show an NVENC warning every time streaming starts.
- **A new install names the host after the PC.**
- **PC audio with nothing playing shows as waiting**, not as a warning, on both
  the host and the device.
- **Security.** Over an unencrypted connection, the device sends the PIN only
  after you press **Send the PIN unencrypted**. Input is tied to the encrypted
  session (both ends 1.1.0). A `prismdesk://` link from outside the app asks
  before connecting unless it matches a saved PC exactly. The PIN entry and the
  QR window are hidden from screenshots. The device's diagnostics file moved to
  the app's private storage, and the device drops old repeated video and audio
  packets. "Check for updates" opens only this repository, and the bug report
  draft no longer carries the device's name. The host limits TLS handshakes and
  accepts TLS 1.2 or 1.3 only.

### Fixed

- **The host could crash right after a device disconnected.**
- **The host could get stuck "negotiating" after a device disconnected, and
  could not be stopped.** It now gives up waiting after 5 seconds and carries
  on. What makes the clean-up stall in the first place is not fixed yet.
- **Touch and pen went to the main monitor** when the virtual display was
  placed to the left of or above it.
- **Black bars above and below the picture** when extending in portrait.
- **A green screen at the start of streaming that cleared when the mouse
  moved.** We fixed the encoder output order we found behind it. It was rare and
  we have not seen it since, but we could not make it happen on demand either.
- **With two devices connected, disconnecting one could change the other's
  screen to 1920×1080.** The host now sets the agreed size again. Why Windows
  changes it is not known.
- **The app could send the PIN of the last PC to a different PC.**
- **The device camera could start without being asked.**
- **Turning on HDR for the virtual display during an SDR stream** made the
  picture grey and washed out.
- **The screen preview in Screen to show was stretched sideways**, so portrait
  and landscape screens looked alike.
- **Saved PCs did not show the HDR and USB badges.**
- **After "Stop the host", the last session said the device had ended it.**
- **The display driver read its settings from a folder any user could create.**

### Known issues

New: **video in a small window can look oversaturated during HDR streaming.**
See [docs/known-issues.md](docs/known-issues.md).

## 1.0.0 — 2026-09-27

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
