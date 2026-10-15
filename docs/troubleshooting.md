# Troubleshooting

Find what you are seeing, then check and fix it in the order given. Messages in
quotes are exactly what the app on the device or the host window on the PC
shows. Both follow your language setting, so they may appear in Japanese
instead.

If your problem is not here, look at [Known issues](known-issues.md), and then
[tell us](#reporting-a-problem).

## Start here: the host checks itself

On the PC, open the host window (the tray icon) and go to the **Connection** tab.
The first section, **Readiness**, checks the PC side for you. When everything is
in order it reads **Ready**. When something is not, it opens the line that
failed and says what to do:

| Line | What it says when something is wrong | What to do |
|---|---|---|
| **Driver** | "not installed. Run the installer again" | Run the PrismDesk installer again. |
| **Device node** | "missing. Stop the host and start it again" | **Stop the host**, then **Start the host** (bottom left of the window). |
| **Driver link** | "the driver is not responding. Restart the PC" | Restart the PC. |
| **Firewall** | "a rule is missing. Run the installer again" | Run the installer again. |
| | "a rule is disabled. Enable it, or run the installer again" | Turn the rule back on in Windows Defender Firewall, or run the installer again. |
| | "a rule points at a different exe. Run the installer again" | Run the installer again. |
| | "a rule's port differs from the settings. Run the installer again, or reset the ports on the Settings tab" | Run the installer again. (The port fields appear on the Settings tab only with **Show details** on.) |
| | "cannot be checked (another firewall seems to be active; allow the 6 ports there)" | Allow the six ports listed in [Set up over Wi-Fi](setup-wifi.md#what-the-installer-opened) in that firewall. |
| **Ports** | "in use by another process. Close that app" | Close the program named next to it. |
| **Auto-start** | "does not start at logon. You can enable it on the Settings tab" | Only matters if you want PrismDesk ready after every sign-in: Settings → **Start automatically when Windows signs in**. While it is off, Readiness shows this line instead of **Ready**; devices can still connect. |

**Show details** (bottom left) shows all seven lines even when they pass. A
screenshot with it on is also what helps most when you report a problem.

## Symptoms

**Finding the PC**

- [The app says "No hosts found yet"](#the-app-says-no-hosts-found-yet)
- [On public Wi-Fi](#on-public-wi-fi)
- [A VPN is on](#a-vpn-is-on)
- [The PC has more than one network adapter](#the-pc-has-more-than-one-network-adapter)
- ["Could not reach the host"](#could-not-reach-the-host)

**Connecting**

- [The host asks for a pairing PIN](#the-host-asks-for-a-pairing-pin)
- ["The certificate of the host is not the one that was expected"](#the-certificate-of-the-host-is-not-the-one-that-was-expected)
- ["A different host answered here"](#a-different-host-answered-here)
- ["Its certificate fingerprint is unknown"](#its-certificate-fingerprint-is-unknown)
- ["The host has reached its connection limit"](#the-host-has-reached-its-connection-limit)
- ["This host requires encrypted connections"](#this-host-requires-encrypted-connections)
- ["Could not open the receive ports"](#could-not-open-the-receive-ports)

**While streaming**

- ["The connection dropped. Reconnecting…"](#the-connection-dropped-reconnecting)
- ["The host is not responding"](#the-host-is-not-responding)
- [The picture does not arrive, or breaks into blocks](#the-picture-does-not-arrive-or-breaks-into-blocks)
- [The tablet shows a copy of the PC's screen](#the-tablet-shows-a-copy-of-the-pcs-screen)
- [No sound on the device](#no-sound-on-the-device)
- [A drawing app ignores the pen](#a-drawing-app-ignores-the-pen)
- [HDR does not come through](#hdr-does-not-come-through)
- [The camera does not work](#the-camera-does-not-work)

**On the PC**

- [The installer is blocked or will not install](#the-installer-is-blocked-or-will-not-install)
- [No virtual display can be created](#no-virtual-display-can-be-created)
- [Closing the window did not quit PrismDesk](#closing-the-window-did-not-quit-prismdesk)
- [Activating Pro fails](#activating-pro-fails)
- ["Could not check for updates"](#could-not-check-for-updates)

## Finding the PC

### The app says "No hosts found yet"

1. **Is PrismDesk running on the PC?** Look for the tray icon. In the host
   window, the button at the bottom left should read **Stop the host**; if it
   reads **Start the host**, press it.
2. **Are both on the same network?** Same router, same subnet. A guest SSID,
   *AP isolation*, or a router that keeps its 2.4 GHz and 5 GHz networks apart
   all hide the PC.
3. **Look at Readiness** on the host's Connection tab ([above](#start-here-the-host-checks-itself)).
   A missing firewall rule hides the PC the same way a wrong network does.
4. **Connect without discovery.** The host's Connection tab shows a QR code and
   a connection string. In the app, tap **Scan a QR code**, or open **Other ways
   to connect (address, USB)** → **Enter a host directly** and paste the string.

The search keeps running while that screen is open; a host appears as soon as
it answers. More in [Set up over Wi-Fi](setup-wifi.md#if-no-host-is-found).

### On public Wi-Fi

Hotel and café Wi-Fi often stops devices from reaching each other, so the PC is
never found. Turn on **Mobile hotspot** on the PC (Windows Settings → Network &
internet) and connect the device to it. The app marks a host reached this way as
**Hotspot**. Pick the 5 GHz band if the PC offers it; the hotspot uses more of
the PC's battery.

### A VPN is on

A VPN on the PC or on the device can hide the PC from discovery, and can also
make a found PC impossible to connect to.

- **The PC is not found.** Discovery does not cross a VPN. Paste the connection
  string from the host's Connection tab into **Enter a host directly**. Once you
  have connected, the app remembers the host.
- **The PC is found, but connecting fails.** The VPN is sending traffic for your
  local network into the tunnel. Let the VPN leave your local network alone (the
  setting is often called *exclude private IPs*, *allow LAN access* or *local
  network sharing*), exclude the PrismDesk app from the VPN, or turn the VPN
  off. We hit this with WireGuard during development; it is a VPN setting, not
  something PrismDesk can change.

### The PC has more than one network adapter

A VPN adapter, a virtual machine network or a second network card all count. The
host's Connection tab then says *"There are 2 adapters. Pick the one on the same
network as the device…"* and lists **Addresses of this host**. Press **Use**
next to the one on the same network as the device. The QR code and the
connection string change with your choice. Prefer **USB (recommended)** when it
is listed.

### "Could not reach the host"

The full message is *"Could not reach the host. Check that PrismDesk is running
there and that both are on the same network."* Go through
[No hosts found yet](#the-app-says-no-hosts-found-yet) — the causes are the same.

If it says *"The host is not answering. The connection went through, but nothing
came back."* instead, the PC was reached but did not finish the connection: look
at Readiness on the host, and at the **Log** tab for a line in red.

## Connecting

### The host asks for a pairing PIN

You see *"A pairing PIN is required."* or *"The pairing PIN does not match."*

The PIN is the six digits shown on the host's Connection tab, to the right of
the QR code. Type it into **Pairing PIN (6 digits)** and press **Reconnect with
this PIN**. Scanning the QR code fills it in for you, and the app remembers it
for next time.

If it keeps failing, someone may have pressed **Generate a new PIN** on the host
(Settings → **Security**): read the PIN on the PC again. After several wrong
PINs, the host turns down every PIN from that device for a while — even the
right one still reads *"does not match"*. Wait a little, then try again.

If the app warns *"This connection is not encrypted. The PIN will be sent in a
form that anyone on the same network can read."*, encryption is turned off on
the host. Turn it on under Settings → **Security** → **Encrypt the traffic** and
start the host again, rather than sending the PIN in the clear.

### "The certificate of the host is not the one that was expected"

The device remembers each PC by its certificate. This message means the PC at
that address now has a different one. Either:

- **You replaced the certificate on the PC** (Settings → Security → **Replace
  the certificate** — the button is shown only with **Show details** on and
  encryption on), or reinstalled in a way that made a new one. Scan the QR
  code on the host again, and enter the PIN again if asked.
- **It is a different PC**, or something on the network is pretending to be
  yours. Do not connect. Check that you are on your own network.

### "A different host answered here"

A host with a different certificate answered at a saved address, often because
the router gave the address to another PC. Connect from that host's own line in
the list. If you replaced the certificate on your PC, scan its QR code again.

### "Its certificate fingerprint is unknown"

The full message is *"This host encrypts its traffic, but its certificate
fingerprint is unknown. Use the QR code or the connection string shown on the
Connection tab of the host."* Do exactly that: the QR code and the connection
string both carry the fingerprint.

### "The host has reached its connection limit"

The host already has as many devices connected as it allows. The free edition
connects **one** device at a time; Pro connects up to four. Disconnect one of
the other devices (in its app, or with **Disconnect** on the host's Connection
tab), then connect again.

### "This host requires encrypted connections"

The full message is *"This host requires encrypted connections. Update the app
on this device."* The app is older than the host. Update it from Google Play.

### "Could not open the receive ports"

The full message is *"Could not open the receive ports (…). Another app may be
using them, or a previous session is still holding them. Restart the app."*
Close the PrismDesk app completely (swipe it away from recent apps) and open it
again.

## While streaming

### "The connection dropped. Reconnecting…"

The app reconnects by itself, and after a short drop the session continues on
the same virtual display. If it gives up with *"Could not reconnect to the host"*,
press **Try again** or connect from the list.

If the connection was gone for longer, a new session starts and Windows builds
the virtual display again. Windows that were on it can come back on the main
monitor; move them back.

Drops that keep happening point at the network: 2.4 GHz Wi-Fi, a weak signal, or
a busy channel. The app itself says *"2.4 GHz Wi-Fi drops out easily. 5 GHz is
recommended."*

### "The host is not responding"

The picture goes black with *"The host is not responding"* and the time since
the last data. Nothing has arrived from the PC for a few seconds. That can be
the PC going to sleep, the host being stopped, or the network dropping out for a
moment — the device cannot tell which.

*"The picture comes back on its own if the host returns."* If the PC is asleep,
wake it; nothing needs doing on the device. To stop waiting, press **Open
controls** and choose **Disconnect**.

### The picture does not arrive, or breaks into blocks

- **Stuck on "Waiting for the picture…" while the PC's screen is off.** We have
  seen the virtual display stop producing frames while the PC's own monitor was
  turned off by power settings. Move the mouse or press a key on the PC to wake
  its screen.
- **The picture breaks into blocks and stays that way.** On the host's
  Connection tab, press **Redraw the screen**. That resends a complete picture.
- **"The decoder could not be started"** on the device. The message names the
  codec and size it tried. Try the app's Settings → **Codec** → **H.264**, or a
  smaller **Virtual display resolution**, and connect again.

### The tablet shows a copy of the PC's screen

You wanted a second desktop, but the tablet shows the same thing as a PC monitor.
Windows has switched the virtual display to *Duplicate these displays*. The host
says so on its Statistics and Log tabs.

- Check that **Always keep the virtual display extended** (host Settings →
  **Virtual display**) is still on — it is on unless someone turned it off — or
- In Windows Settings → System → Display, choose **Extend these displays**.

If you chose **Mirror** in the app on purpose, that is what Mirror does; switch
the app's Settings → **Display mode** to **Extend**.

### No sound on the device

- **Audio is decided before connecting.** In the app, check Settings →
  **Audio**, and connect again. It cannot be switched during a session.
- **Is anything playing on Windows?** The host's Statistics tab says *"Audio:
  idle (nothing is playing on Windows)"* when there is nothing to send — that is
  not a fault.
- *"Silent: audio is being sent, but it is all zeros. Check the playback device
  on Windows"* — Windows is playing to a device PrismDesk is not listening to,
  or you have just switched the playback device. Check the playback device in
  Windows sound settings.

### A drawing app ignores the pen

Set the app's tablet input to **Windows Ink** instead of WinTab. Exact steps for
Krita are in [Pen](pen.md). The device also says so the first time the pen
touches: *"Pen input received. If your drawing app ignores the pen, set its
tablet input to Windows Ink."*

### HDR does not come through

After connecting, the app lists what the host changed and why. Find the reason
here:

| The app says | What to do |
|---|---|
| "HDR is part of PrismDesk Pro. This host is running the free edition, so it will send SDR." | HDR needs Pro on the PC. |
| "This device cannot show HDR, so the host is sending SDR." | The device cannot use HDR. See [HDR](hdr.md). |
| "HDR needs H.265, so the host is sending SDR." | In the app, set Settings → **Codec** to **H.265** or **Default**. |
| "Windows could not turn on HDR for the virtual display, so the host is sending SDR." | On the PC, open Settings → System → Display, select the PrismDesk display and turn on **Use HDR**. |
| "The encoder for this screen cannot output H.265, so the host is sending H.264." | The PC's encoder cannot do HDR. See [Known issues](known-issues.md#hdr-is-unavailable-on-some-intel-only-pcs). |

**HDR arrives but looks like SDR.** Some panels cannot get brighter than SDR; the
app says so under **Color space**. See [HDR](hdr.md#devices-whose-panel-cannot-use-it).
To check what is really being sent, turn on **Show details** on the host and
read **HDR as measured** on the Connection tab.

### The camera does not work

- *"Using the device camera as a webcam is part of PrismDesk Pro."* The camera
  needs Pro on the PC.
- **No Camera button on the device.** Check that **Publish the camera of the
  device as a Windows virtual camera** (host Settings → **Virtual camera**) is
  still on — it is on unless someone turned it off.
- *"Camera permission has not been granted."* Press **Open app settings** and
  allow the camera for PrismDesk.
- **PrismDesk Camera is not in an app's camera list.** Close that app and open it
  again — apps read the camera list when they start. More in
  [Webcam](webcam.md#prismdesk-camera-is-not-in-the-list).
- **The Windows Camera app cannot save photos** (`0xA00F424F`). That is a Windows
  library problem, not the camera. The fix is on the [Webcam](webcam.md) page
  (*Photos will not save*).

## On the PC

### The installer is blocked or will not install

- **"Windows protected your PC".** See [SmartScreen](smartscreen.md) for what to
  check before you press *Run anyway*.
- **It stops on Windows 10.** PrismDesk needs Windows 11 (build 22000 or later).
  This is deliberate.
- **"The virtual display driver could not be installed."** The reason is in
  `setup.log` in the PrismDesk folder, which the message names. Run the
  installer again; if the same message comes back, [report it](#reporting-a-problem)
  with that file.
- **"The firewall rules could not be added."** PrismDesk still installs, but
  Windows may ask whether to allow it the first time a device connects — say
  yes. Running the installer again retries the rules.
- **"Windows does not trust whoever signed the PrismDesk display driver"
  (0x800B0109).** The installer you have is not a release build. Download the
  installer from the [Releases page](https://github.com/Asynchronous-0x4C/prismdesk-app/releases).

### No virtual display can be created

- *"The driver is not installed, so no virtual display can be created. Run the
  PrismDesk installer again."* Do that.
- *"Could not create the virtual display device (no administrator rights)."*
  PrismDesk needs administrator rights to create a display. Start it from the
  Start menu and accept the Windows prompt, or let the sign-in start-up entry
  start it.
- Readiness says *"the driver is not responding. Restart the PC"*. Restart the
  PC. We have seen this after the PC's own monitor was turned off while a device
  was connected.

### Closing the window did not quit PrismDesk

That is on purpose: closing the window leaves PrismDesk in the tray, still
listening for devices. To quit, right-click the tray icon → **Exit**.

### Activating Pro fails

| The host says | What to do |
|---|---|
| "That does not look like a license key." | Paste the key starting with `PDESK-` from your purchase email. |
| "This key has reached its device limit." | One key covers three PCs. Release a PC you no longer use from the Polar purchase page. |
| "Could not reach Polar. Check the internet connection and the firewall." | Activation needs the internet once. After that, Pro works offline. |
| "Too many attempts. Wait a while and try again." | Wait, then try again. |

For anything about an order, write to [support@prismdesk.app](mailto:support@prismdesk.app)
rather than a public issue.

### "Could not check for updates"

The full message is *"Could not check for updates. Check that this PC is
connected to the internet."* **Check for updates** fetches one small file from
https://prismdesk.app when you press it, and nothing else. The latest version is always on
the [Releases page](https://github.com/Asynchronous-0x4C/prismdesk-app/releases).

## Reporting a problem

Two things make a report useful: the diagnostics file, and a screenshot of the
host with **Show details** on.

- **On the PC:** Log tab → **Export diagnostics** writes one file under
  `%LOCALAPPDATA%\PrismDesk\`; **Open folder** shows it. **Report a problem**
  opens a draft GitHub issue with the version, Windows build and GPU filled in.
- **On the device:** Settings → **Report a problem** → **Share diagnostics**, and
  choose where the file goes. It contains no PIN and no authentication token.

Open the issue from one side only, at [Issues](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose), and
attach the files. Anything with an order number, a licence key or personal data
goes to [support@prismdesk.app](mailto:support@prismdesk.app) instead.

See also: [Known issues](known-issues.md) · [FAQ](faq.md) ·
[Set up over Wi-Fi](setup-wifi.md)
