# Security

PrismDesk installs a display driver on your PC and moves your screen across
your network. A security report is worth more to us than a feature request, and
this page says where to send one.

## Reporting something

**Email [support@prismdesk.app](mailto:support@prismdesk.app) with `security` in the
subject line.** Please do not open a public issue for a problem that could be
used against other people before there is a fix for it.

Include whatever you have:

- What you did, in enough detail that we can do it too.
- The PrismDesk version on the PC and on the device. The host window shows the
  PC's version in its title bar.
- The Windows build and the Android device, when they are part of it.
- What you think it gets an attacker.

If you would rather not send the details in the clear, say so in a first message
with nothing sensitive in it and we will agree on another way.

## What happens after that

**PrismDesk is built by one person. There is no security team, and this page
does not promise a response time** — a number we could not keep would be worse
than no number at all.

What we can say:

- A person reads it and a person answers it.
- If it is real, we tell you what we intend to do and when we expect it done —
  once we know, not before.
- The fix ships in a normal release. The release notes say that a security issue
  was fixed and credit you by whatever name you give us, unless you would rather
  not be named.
- **There is no bug bounty and no payment.** Better to know that before you spend
  a weekend on it than after.

## Which versions get fixes

**The current release, and nothing older.** There is one release line and no
back-ports; upgrading is the fix.

## In scope

- The Windows host, **including the PrismDesk virtual display driver.** It is a
  user-mode driver (IddCx) and not a kernel driver, but it is still a driver we
  ask you to install.
- The Android app.
- What runs between them: discovery, the TLS 1.3 control and input channels, and
  the AES-256-GCM video, audio and camera channels.
- The installer, and the firewall rules and start-up entry it creates.
- [https://prismdesk.app](https://prismdesk.app) and anything served from it.

Our payment provider and Google Play are not ours to secure. Report those to
them.

## Working as intended

These are true on purpose, and are written down here so that nobody spends a
weekend proving them:

- **A device that can reach the PC, and has the certificate fingerprint from the
  QR code or the connection URI, can connect to it.** Both are shown on the PC's
  own screen, so anyone who can see your screen can read them.
- **PrismDesk injects real touch, pen and keyboard input into Windows.** That
  is the product, not a flaw — a connected device drives the PC.
- **The installer asks for administrator rights**, then adds a display driver,
  six inbound firewall rules and a start-up entry. It says so before it does it,
  and [docs/setup-wifi.md](docs/setup-wifi.md) lists the ports.
- **Nothing leaves your network and we run no servers the apps talk to.** There
  is no account to take over — and, equally, nothing we can revoke for you
  remotely.
- **The exported diagnostics file describes your PC and your network.** Read it
  before you attach it to a public issue.

## Not a security report

Crashes, hangs, "it does not work on my tablet" and anything else that is simply
broken belong in the [issue tracker](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose) instead. They get
looked at sooner there, and in public, where the next person can find the answer.
