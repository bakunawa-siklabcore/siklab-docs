# Your Data

The precise version, because this is the question people ask before they trust a tool with their
work — and because the easy answer is an overstatement.

---

## Siklab runs on your machine

There is no Siklab server holding your projects. Your work, your database and your
credential-encryption key live in `~/.siklab`, readable only by your account. Every agent run — the
scoping, the design, the build, the checking — happens locally.

---

## But "runs on your machine" is not "nothing ever leaves your machine"

Four things do. This is the complete list.

### 1. Your brief and relevant code go to your AI provider

Siklab has no AI model and no API key of its own. It drives the CLI **you** installed and signed in
to, or an API key **you** supplied. When an agent works, your brief and the relevant code go to that
provider.

That exchange is between you and them, under your agreement with them. Siklab is not a party to it,
never sees the content, and never sees your credentials.

**This is how the product works, and there is no version of it that doesn't.** A tool that builds
software with AI has to send the work to the AI. What Siklab controls is that the provider is
*yours* — your account, your terms, your choice of which one.

### 2. Update checks

The app asks a release endpoint whether a newer version exists. Like any web request, this carries
your IP address. It does not carry anything about your projects.

### 3. Problem reports — only when you send one

Nothing is reported automatically. When you choose **Report a problem**, it attaches your version,
your OS, and a screenshot if you add one. Reports become entries in a private issue tracker.

!!! danger "Reports are not automatically redacted"
    Do not put API keys, passwords, licence keys, private keys or customer data in a report. Nobody
    at Siklab will ever ask you for any of those.

### 4. Licence activation and renewal

Activating a licence, and the periodic renewal that keeps it valid, are recorded. That is what makes
a licence a licence.

---

## What is never collected

**No product analytics. No telemetry.** No tracking pixels, no session recording, no usage beacons,
no "anonymous usage statistics."

Specifically never collected: your source code, your prompts, your project content, your generated
output.

---

## Your credentials

If you connect an API key, it is encrypted on your machine and never sent to us.

If you use a CLI instead, Siklab never touches your credentials at all — you are signed in through
that tool, and it holds its own authentication.

---

## Who processes what

| | |
|---|---|
| **Your AI provider** | Receives your briefs and code, under your agreement with them |
| **Paddle** | Merchant of record — handles payment, tax and invoicing |
| **Cloudflare** | Serves updates and validates licences |
| **Siklab Core** | Holds licence records and any problem reports you send |

Nobody else.

---

## What you can do about it

- **Choose your provider.** Different providers have different data-retention and training terms.
  Read the one you connect — they vary a lot, and free tiers vary most.
- **Run locally.** An engine like `ollama` keeps the AI step on your machine too.
- **Take your work anywhere.** Everything is in ordinary folders (`~/.siklab/workspaces/`) in
  ordinary formats. Nothing is locked or proprietary.
- **Remove everything.** See [Uninstalling](uninstalling.md). There is no account to close.

---

## The full notice

This page is the plain-English version. The complete Privacy Notice ships **inside the app** — you
are shown it before you accept the licence, and it is available any time from Settings. It is served
from your own install rather than linked, so it works offline and what you read is the document that
actually shipped with your version.
