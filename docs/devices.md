# Devices

Two tables. **The first is what we ran ourselves. The second is what other people
reported.** They are not merged, because they are not the same kind of claim.

## Tested here

Five Android devices. Everything in this table was seen on the machine, not
inferred.

| Device | Android | What was seen |
|---|---|---|
| **Lenovo Idea Tab Pro** (TB373FU) | 16 | The main measurement device. Bandwidth, idle rate, frame timing and every recovery test were measured on it, at 1840×2944. Also one of the four in the four-at-once test. **HDR has not been measured on this device.** |
| **Google Pixel 9** | — | **HDR10 end to end**, twice (`hdrSdrRatio` 7.999703, BT.2020/PQ, no downgrade). Also one of the four in the four-at-once test. |
| **Google Pixel 6** | — | One of the four in the four-at-once test. Also used against a second PC (below). |
| **Google Pixel 3** | — | One of the four in the four-at-once test. |
| **TCL Tab 11 Gen2** | 14 | Connects and shows the screen. That is all that was checked — nothing was measured on it. The only budget device so far. |

**Four at once** means Pixel 3, Pixel 6, Pixel 9 and the Idea Tab Pro connected
to one PC simultaneously, extending the desktop, playing video, at 30–35 Mbps
total and about 50% GPU, with nothing breaking.

Pen and camera were verified on this rig as features
([pen](pen.md), [webcam](webcam.md)), but not device by device, so there is no
per-device column for them yet.

## Reported by other people

Nothing yet — PrismDesk is not out.

Reports arrive as [device reports](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new?template=device-report.yml)
and are copied into this table by hand, with the issue number, so that where a
line came from stays visible. **"It just works" is worth reporting**: this table
is as much about coverage as about faults.

| Device | Android | Result | Report |
|---|---|---|---|
| — | — | — | — |

## PCs

| | |
|---|---|
| **Measurement rig** | Intel Core i7-11700, NVIDIA RTX 3060 + Intel UHD 750, Windows 11 (build 26200), gigabit Ethernet. Every published number comes from this machine. |
| **Also seen working** | An Intel Core Ultra 7 258V laptop, with the Pixel 6. Nothing was measured on it, and which encoder it used was not recorded, so nothing is claimed about it. |

## Not tested

- **Budget hardware, beyond one tablet.** The TCL Tab 11 Gen2 above is the only
  low-cost device tried, and only for the basics. Try the free edition on your own
  device before you pay for anything.
- **iPads, iPhones, macOS, Linux, Windows 10.** Not supported, not planned for
  1.0.
- **Anything below Android 8.0 (API 26)**, or without a hardware H.264 decoder.

See also: [HDR](hdr.md) · [Pen](pen.md) · [Known issues](known-issues.md)
