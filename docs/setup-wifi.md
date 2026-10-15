# Set up over Wi-Fi

This is the normal way to use PrismDesk. Nothing has to be configured on your
router, and there is no account to create.

## First time

1. **Run the installer on the PC** and let it finish. It adds the display driver,
   the firewall rules and the start-up entry itself. Windows will probably warn
   about the installer first — see ["Windows protected your PC"](smartscreen.md)
   for what to check before you run it.
2. **Install PrismDesk on the Android device** from Google Play (or the APK on
   the [Releases page](https://github.com/Asynchronous-0x4C/prismdesk-app/releases)).
3. **Make sure PrismDesk is running on the PC.** If you left *Start PrismDesk
   when I sign in to Windows, ready to accept a tablet* ticked during setup, it
   already is — look for the tray icon. Closing the host window does not stop
   it; it stays in the tray.
4. **Open the app on the device.** Hosts on the same network appear by
   themselves. Tap one and it connects with your saved settings.

That is the whole setup. The two only have to be on the same network — the same
router, and the same subnet.

The host window checks its own side for you: the **Connection** tab starts with
**Readiness**, which reads **Ready** when the driver, the firewall rules, the
ports and the sign-in start-up entry are all in order, and names the part that
is not when something is wrong. (If you unticked the start-up entry, that line
stays open; devices can still connect.)
See [Troubleshooting](troubleshooting.md#start-here-the-host-checks-itself).

## If no host is found

The app says **"No hosts found yet"**, and **If it doesn't show up** opens a list
of what to check. In the order that actually turns out to be the answer:

| Check | What it looks like |
|---|---|
| **Is PrismDesk running on the PC?** | No tray icon, or hosting was stopped from the host window. |
| **Are both on the same network?** | A guest SSID, AP isolation, or a 2.4 GHz and a 5 GHz network that the router keeps apart will all hide the PC. So will a PC on Ethernet and a tablet on a Wi-Fi network that the router treats as a separate segment. |
| **Hotel or café Wi-Fi** | These networks often stop devices from reaching each other. Turn on **Mobile hotspot** on the PC and connect the device to it; the app marks a host reached this way as *Hotspot*. The hotspot uses more of the PC's battery. |
| **Is a VPN running?** | A VPN on either end can swallow discovery. We hit this during development: with the VPN up, nothing was found; with it down, the host appeared immediately. You can still connect without discovery — see below. |
| **2.4 GHz** | It works, but it drops out easily and we do not recommend it. The app says so on the same screen. |

The search keeps running while that screen is open, so a host appears as soon as
it answers.

## Connecting without discovery

Discovery is a convenience, not the only route. The host window's **Connection**
tab shows two things that work even when nothing is found:

- **A QR code.** In the app, tap **Scan a QR code**.
- **A connection string** (`prismdesk://…`, with a **Copy** button next to it).
  In the app, open **Other ways to connect (address, USB)** → **Enter a host
  directly**, and paste it.

**Use one of these two rather than typing a bare address.** Both carry the PC's
certificate fingerprint (`fp=`), so the device can tell your PC from anything
else that answers on the network; the app then marks the host **Verified**. An
address typed by hand does not carry it: the app trusts whatever fingerprint
answers at that address the first time, and marks the host only **Encrypted**.

If the PC has more than one network adapter — a VPN adapter counts as one — the
Connection tab lists **Addresses of this host** and asks which one to hand out,
and the QR code changes with your choice. Pick the address on the same network
as the tablet.

## What the installer opened

PrismDesk listens on six ports, and the installer adds one inbound firewall
rule for each:

| Port | | |
|---|---|---|
| 45100 | UDP | Discovery — how the app finds the PC |
| 45101 | TCP | Control (TLS 1.3) |
| 45102 | TCP | Input — touch, pen, keyboard (TLS 1.3) |
| 45103 | UDP | Video, and the heartbeat that keeps the session alive (AES-256-GCM) |
| 45104 | UDP | Audio (AES-256-GCM) |
| 45105 | UDP | From the device: heartbeat replies, resend requests, and the camera (AES-256-GCM) |

Nothing has to be forwarded on the router — these are for the local network
only. If a third-party firewall asks whether to allow PrismDesk, say yes; if
you removed the rules, running the installer again puts them back.

## More than one device

With **PrismDesk Pro**, four devices can be connected to one PC at the same
time, sharing a single capture and a single encoder. Four is the number that was
verified — see [devices.md](devices.md) — so four is the number we publish. The
free edition connects one device at a time.

## On a laptop

Turning on USB tethering can drop the laptop's own Wi-Fi connection. If you use
both, expect to pick one — see [Set up over USB](setup-usb.md).

See also: [Set up over USB](setup-usb.md) · [Troubleshooting](troubleshooting.md) ·
[Known issues](known-issues.md)
