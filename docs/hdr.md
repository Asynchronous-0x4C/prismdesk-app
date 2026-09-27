# HDR

HDR content on the PC can arrive as HDR content on the tablet — not tone-mapped
down and re-labelled, but BT.2020 with a PQ curve, end to end.

You do not switch it on. Both ends check what they can do and pick HDR when it
would actually look different, and PrismDesk tells you which part is missing
when it does not.

## What has to be true

| | |
|---|---|
| **The device can decode HEVC Main10** | HDR10 rides on H.265. There is no HDR over H.264. |
| **The device's display reports HDR10 or HLG** | This is what Android reports about the panel, not what the panel is worth. |
| **The panel can go brighter than SDR** | Android reports the ratio. If it tops out at 1.0, HDR10 would look exactly like SDR, so the default stays SDR. |
| **The PC can encode 10-bit** | Asked once when the host starts. A GPU that cannot do it keeps HDR off rather than failing every time you connect. |

If either of the first two is missing, the app says which one:

- *This device can neither decode HEVC Main10 nor show HDR.*
- *The display supports HDR, but HEVC Main10 cannot be decoded.*
- *HEVC Main10 can be decoded, but the display does not report HDR10 or HLG.*

The **Color space** setting in the app says what the automatic answer will be on
the device you are holding — *This device will get HDR10* or *This device will
get SDR* — before you connect. **SDR and HDR10 are still there to choose**, and
choosing HDR10 on a panel that cannot use it is allowed; the app just tells you
what will happen.

## "HDR is on" and "HDR arrived" are different claims

Windows can be in HDR mode while what actually gets captured is an SDR image
carrying an HDR label. That failure looks like success from every switch and
checkbox on the machine, which is why the host measures it instead of trusting
the settings.

On the PC: host window → tick **Show details** in the sidebar → the
**Connection** tab gains an **HDR as measured** section, with a *re-measure*
button. That readout is the answer to "am I really getting HDR", and it is taken
from the picture rather than from the configuration.

## Devices whose panel cannot use it

A device can satisfy every condition above and still show you nothing new.
Android reports how much brighter than SDR a panel can go, and on some panels
that ratio is 1.0 — HDR10 will be sent and decoded, and it will look exactly like
SDR.

That is why the automatic choice looks at the ratio and not only at "can decode,
can display". Devices older than Android 16 cannot report their limit at all, and
those stay on SDR too — a limit that cannot be read is not a limit that has been
met. The app says so where you choose:

> *This panel cannot reach HDR brightness (its HDR/SDR ratio tops out at 1.0).
> HDR10 will be sent, but it will look as bright as SDR.*

## What was measured

On a **Google Pixel 9**:

| | |
|---|---|
| `hdrSdrRatio` | **7.999703** (SDR would be 1.0) |
| Colour space, requested and produced | **BT.2020 / PQ / limited** — no silent downgrade at either end |
| SDR white, luma code value | expected 588, measured **588** |

On the same PC, same screen, 2944x1840 at 60 Hz, ultra-low-latency profile:

| Session | Frame rate | Bit rate |
|---|---|---|
| H.265, HDR10 | 38 fps | **2,800 kbps** |
| H.265, SDR | 38 fps | 6,800 kbps |
| H.264, SDR | 38 fps | 7,100 kbps |

**HDR10 used less bandwidth than SDR here, not more.** One run per row, one PC,
one picture on screen; treat it as "HDR does not cost bandwidth on this material"
rather than as a rate you can plan around.

Starting a session took **0.97 s with HDR and 0.82 s without** — the same
measurement, one run each.

**What has not been measured:** GPU load with HDR against SDR, and bandwidth on
moving content. Neither is claimed anywhere.

See also: [Devices](devices.md) · [FAQ](faq.md)
