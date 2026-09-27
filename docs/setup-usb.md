# Set up over USB

PrismDesk has no separate USB mode. What you do is turn on **USB tethering**
on the Android device: the cable becomes a network the PC is on, and everything
else works exactly as it does over Wi-Fi.

Use it when the Wi-Fi is crowded, when you would rather not be on Wi-Fi at all,
or when the tablet needs to charge anyway.

## Turning USB tethering on

Plug the device into the PC first. On most Android devices the switch cannot be
turned on until a cable is attached.

| Device | Where the switch is |
|---|---|
| **Google Pixel 9** | Settings → Network & internet → Hotspot & tethering → **USB tethering** |
| **Lenovo Idea Tab Pro** | Settings → Additional connections → Tethering → **USB tethering** |
| Anything else | Search the system settings for *USB tethering*. It is usually under tethering or hotspot. |

The app helps here: the connection screen shows **"USB tethering: on (hosts over
USB are searched too)"** or **"USB tethering: off"** with an **Open settings**
button that jumps straight to the tethering screen. From that jump you land one
level in — **Hotspot & tethering → USB tethering** on a Pixel.

Then tap **Search again** in the app. The PC appears the same way it does over
Wi-Fi.

## What changes

| | |
|---|---|
| **Wi-Fi can be off.** | The connection keeps working over the cable. |
| **Connecting over Wi-Fi stops working** while tethering is on. | The PC is reached over the cable instead. |
| **Charging still works.** | You can use the tablet over USB and charge it at the same time. |
| **On a laptop**, turning on USB tethering can drop the laptop's own Wi-Fi connection. | Windows may prefer the new connection. If the laptop needs Wi-Fi for other things, this is the trade. |

## If it does not connect

1. **Check that USB tethering is actually on.** It switches itself off when the
   cable is unplugged, and it stays off when you plug the cable back in.
2. **Tap "Search again"** in the app. Discovery does not retry forever on its
   own.
3. **If it still hangs, suspect a VPN first.** During development a VPN on the PC
   had to be disabled before anything would connect — over the cable as much as
   over Wi-Fi.
4. If none of that helps, the problem is more likely on the PC side than in the
   cable; see [Set up over Wi-Fi](setup-wifi.md) for what else hides a host, and
   open an [issue](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose) with the diagnostics attached.

See also: [Set up over Wi-Fi](setup-wifi.md) · [Known issues](known-issues.md)
