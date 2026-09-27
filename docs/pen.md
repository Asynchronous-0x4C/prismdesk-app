# Pen

Pressure, tilt and rotation from the device's stylus arrive on the PC as **real
Windows pen input** — the same kind of input a pen display produces — so
pressure-sensitive apps see a pen and not a mouse.

## What arrives

| | |
|---|---|
| **Pressure** | Verified. |
| **Tilt** | Verified. |
| **Rotation** (barrel roll) | Verified. |

What PrismDesk injects is **Windows Pointer Input**, which is what Windows Ink
is built on. **It is not WinTab.** That distinction is the single thing worth
knowing on this page, because it decides whether an app sees the pen at all.

## If an app ignores the pen: switch it to Windows Ink

Some drawing applications default to **WinTab**, the older Wacom-era interface.
An app looking only at WinTab sees no pen at all — not a pen without pressure, but
no pen. Every value looks broken at once, which is the giveaway.

**Krita** (verified):

> Settings → Configure Krita… → **Tablet Settings** → *Tablet Input API* →
> **Windows Ink**, then restart Krita.

With WinTab selected, pressure, tilt and rotation were all dead. With Windows
Ink selected, all three worked. Nothing on the PrismDesk side had to change.

Photoshop, Corel Painter and Clip Studio Paint have a comparable switch (usually
worded as *use Windows Ink* or *WinTab / Windows Ink*). **We have not tested
those** — if you try one, a [device report](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new?template=device-report.yml)
or a note in [Discussions](https://github.com/Asynchronous-0x4C/prismdesk-app/discussions) is welcome, and it will end up on
this page.

Browsers use Pointer Input directly and need no setting: pressure, tilt and
rotation all worked there out of the box.

## Two things we have not measured

Both are honest gaps, not complaints about your hardware:

- **Tilt at shallow angles feels weaker than it should.** The tilt maths uses a
  linear approximation, which is consistent with that impression — but it is an
  impression from drawing, not a measurement.
- **Turning the pen's direction of lean does not rotate the brush.** That is the
  correct behaviour (rotation should follow barrel twist, not lean direction),
  and it matched expectations on the machine — but the code path suggests it
  should be checked properly, and it has not been.

**Latency is not published anywhere in PrismDesk**, pen included, because it
has not been measured in a way worth publishing.

See also: [Devices](devices.md) · [Known issues](known-issues.md)
