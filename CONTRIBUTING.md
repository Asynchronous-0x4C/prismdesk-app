# Contributing

**Pull requests are not accepted, because the product source is not here.** This
repository holds the documentation, the issue tracker and the releases; there is
nothing in it to patch. That is also why there is no `good first issue` label —
labelling work that does not exist would be a lie.

What does help, and what is actually used:

| | |
|---|---|
| **Something is broken** | [Bug report](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose) |
| **It works — or does not work — on your tablet or phone** | [Device report](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose). Good news counts as much as bad news; [docs/devices.md](docs/devices.md) is built from these |
| **Something PrismDesk should do and doesn't** | [Feature request](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose) |
| **A question, or "does it work with X?"** | [Discussions](https://github.com/Asynchronous-0x4C/prismdesk-app/discussions) |
| **A security problem** | [SECURITY.md](SECURITY.md) — by email, not in a public issue |
| **An order number, a licence key, or anything personal** | [support@prismdesk.app](mailto:support@prismdesk.app). Issues here are public and stay public |

## Issue or discussion?

**An issue is something to fix or decide. A discussion is everything else.**

| Category | For |
|---|---|
| **Q&A** | "How do I…", "Why does…", "Does it work with…". |
| **Ideas** | Half-formed suggestions, before they are an issue. |
| **Show and tell** | What you use it for, and what it looks like. |
| **Announcements** | Releases. Read-only. |

When you are not sure, ask in Discussions. Turning a discussion into an issue is
easy; an issue nobody can close is not.

## Before you open an issue

- **Search the existing issues** and [docs/known-issues.md](docs/known-issues.md).
- **Use a template.** Blank issues are switched off — not to be awkward, but
  because the first reply to a report without a version number and a Windows
  build is always a request for the version number and the Windows build.
- **One problem per issue.** Two problems in one thread means one of them gets
  forgotten.
- **No licence key, order number, email address or public IP address.** Look
  through an exported diagnostics file before you attach it.

## Feature requests

PrismDesk is built by one person, so the honest answer to most requests is "not
soon", and saying that up front is better than a silent backlog. **What gets
built first is what fixes a problem several people have** — so describe the
problem you hit, not only the feature you thought of. The problem is the part
that can be solved another way.

Some things are decided and will not change. The frame rate is not advertised,
end-to-end latency is not published, and there is no macOS, Linux or iPad
version. [docs/faq.md](docs/faq.md) explains each of those.

## Documentation

Wrong or confusing instructions in `docs/` are worth reporting like any other
bug. **Do not send a pull request against those files** — they are published
copies, regenerated when a release goes out, so an edit made here would be
overwritten. Say what is wrong and it gets fixed where it comes from.

## Translations

The apps ship in English and Japanese. There is no translation workflow to
contribute to yet, but a wrong or awkward string in either language is a good
issue.

## Behaviour

[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). It is short.
