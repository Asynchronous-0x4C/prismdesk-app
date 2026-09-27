# "Windows protected your PC"

The first time you run the PrismDesk installer, Windows is likely to show a
blue box:

> **Windows protected your PC**
> Microsoft Defender SmartScreen prevented an unrecognised app from starting.
> Running this app might put your PC at risk.

Clicking **More info** reveals the app name, the publisher, and a **Run anyway**
button.

This page is not here to tell you to press it. It is here to tell you what you
can check first, because "just click through the warning" is exactly the habit
that gets people hurt.

## Why it appears

SmartScreen is a **reputation** check, not a signature check. A file that few
people have downloaded yet is unrecognised, and that is true even when it is
correctly signed by a certificate from a public authority. Reputation
accumulates as more people install the same signed file; a new publisher starts
at zero and cannot buy its way past it.

So: the warning going away is a matter of time, and its presence says nothing
about whether this particular file is what it claims to be. **That question you
can settle yourself, right now.**

## What you can check

**1. The publisher.** In the SmartScreen box, click *More info* — the publisher
line comes from the digital signature, not from the file name. You can see the
same thing before running it: right-click the installer → **Properties** →
**Digital Signatures**.

The publisher line has to read **Masato Okumura**. That is the name on the
certificate PrismDesk is signed with — an **individual-validation (IV) code
signing certificate issued by SSL.com**, not an EV certificate. If *More info*
shows any other name, or says "Unknown publisher", the file you have is not the
one we published: do not run it, and
[tell us](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose).

An IV certificate means a certificate authority checked the identity of one
named person, rather than a registered company. It does not carry the
reputation head start that an EV certificate does, which is why SmartScreen
still warns about the first few downloads.

**2. The hash.** Every release includes `SHA256SUMS.txt`. Compare it with what
you downloaded:

```powershell
Get-FileHash .\PrismDesk-Setup.exe -Algorithm SHA256
```

The line for that file in `SHA256SUMS.txt` has to match, character for
character. Download both from the same place —
[https://github.com/Asynchronous-0x4C/prismdesk-app/releases](https://github.com/Asynchronous-0x4C/prismdesk-app/releases) — and if they ever disagree, do not run the
file, and [tell us](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose).

**3. A second opinion.** Uploading the installer to VirusTotal is a reasonable
thing to do with any executable from a small vendor, ours included.

## The UAC prompt is a separate thing

After SmartScreen, Windows asks for administrator rights. That one is not about
reputation — the installer genuinely needs them, because it:

- installs the virtual display driver into the Windows driver store,
- adds six inbound firewall rules (one per port — see
  [Set up over Wi-Fi](setup-wifi.md)),
- registers the virtual camera,
- creates the sign-in start-up entry, if you left that ticked.

Uninstalling reverses all four.

## What we do not do about it

We do not ask you to disable SmartScreen, and we do not ship instructions for
turning it off. It is doing its job; it just does not know us yet.

See also: [FAQ](faq.md) · [Known issues](known-issues.md)
