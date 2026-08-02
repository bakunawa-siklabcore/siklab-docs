# Questions people actually ask

Short answers, with links where there is more. If something here disagrees with what the app tells
you, the app is right — it knows your version and your licence.

---

## Buying and trying

**Do I need a credit card to try it?**
No. No card and no account. The trial is unlocked — no restricted features and no project limit.

**When does the trial clock start?**
On your **first build**, not on download and not on install. You can install today and start the
clock next week.

**What happens when the trial ends?**
Nothing is taken away. Everything you already built stays on your machine and stays openable,
runnable and exportable. A plan is needed only to *start* something new.

**What does it cost?**
$39/month, or $199/year while founding seats last, then $249/year. Prices exclude tax — Paddle adds
it at checkout based on where you are. See [the pricing on the site](https://siklabcore.com/#pricing).

**Is the annual plan a subscription or a one-off?**
A subscription. Both plans renew.

**Is there a money-back guarantee?**
No blanket guarantee. The trial is the decision mechanism, which is why it is unlocked. If something
has genuinely gone wrong, email support and we will sort it out.

**Who am I actually paying?**
Paddle, as merchant of record. They handle the payment, the tax and the invoice.

**How many machines can I use?**
Two devices on one seat.

---

## What it needs

**Do I need to buy an AI subscription too?**
You need *an* AI — Siklab contains no model and no API key of its own. If you already have an AI
coding assistant installed and signed in, Siklab uses it and there is nothing more to buy. Otherwise
an API key works.

**Which AI should I use?**
`claude` or `codex`. Others work but throw provider errors more often, which shows up as a build
that stalls. See [Known Issues](known-issues.md).

**Does it run on Windows?**
Not natively. It runs on Windows through WSL2, using the Linux build. See
[Requirements](requirements.md).

**Does it work offline?**
The app does. The building does not — your AI provider is on the internet.

**Will it run on my machine?**
macOS on Apple Silicon is the tested platform. Linux and WSL are beta and need a CPU with AVX2. The
honest matrix is on [Requirements](requirements.md).

---

## What happens to my code

**Does my code go to a Siklab server?**
No. There is no Siklab server holding your projects. Your work, your database and your credential
key are in `~/.siklab` on your own machine.

**So nothing ever leaves my machine?**
That would be an overstatement, and here is the precise version. Four things leave: **your brief and
relevant code go to your AI provider** through the CLI you installed and signed in to, under your
agreement with them — Siklab is not a party to it and never sees the content; **update checks**;
**problem reports**, only when you choose to send one; and **licence activation and renewal**.

**Is there analytics or telemetry?**
None. No product analytics, no tracking pixels, no session recording, no usage beacons. Your source,
prompts, project content and generated output are never collected.

**Do you store my API key?**
It is encrypted on your machine and never sent to us.

---

## What I own

**Can I sell what it builds?**
Yes. Source, assets, documentation — including anything built during the trial. Use it, change it,
host it, sell it. No royalty, no attribution, and none of Siklab's code is inside it.

**Do I need Siklab installed for my app to run?**
No. Exported applications need no Siklab component.

**Is there a catch?**
One honest one: generated projects usually pull in third-party libraries under their own licences.
Siklab cannot grant rights it does not have — check those before shipping commercially.

**Do I own Siklab itself?**
No. It is licensed to you, not sold. Run it, yes. Redistribute it, resell it, host it as a service,
or extract its agents and prompts, no.

---

## Using it

**Do I need to know how to code?**
No. You describe what you want and approve a design. Reading the result helps but is not required.

**How long does a build take?**
A small app is minutes. Something with several screens takes longer. You do not need to watch it.

**Can I change my mind after seeing the design?**
That is what the design step is for. Nothing is built until you approve a mockup, and changing your
mind there is free.

**What if the finished app is wrong?**
Say what is wrong in plain words. It goes back to be fixed and returns as a new version.

**Does it deploy or host my app?**
No. It builds and hands over; where it runs is your call.

**Is the generated code guaranteed to work?**
No, and anyone claiming otherwise about an AI tool is selling something. Siklab tells you what it
checked and what it could not confirm. Review anything you are going to rely on.

**Where do my files end up?**
`~/.siklab/workspaces/` — ordinary folders you can open in any editor. Nothing is locked or in a
proprietary format.

---

## When it goes wrong

**A build seems stuck. Is it broken?**
Usually the AI engine, not Siklab. Start with [Troubleshooting](troubleshooting.md).

**I forgot my password.**
`cd ~/.siklab-core && ./siklab-api-<platform> recover` prints a one-time key, valid 15 minutes.
There is no reset email because there is no account.

**How do I uninstall?**
[Uninstalling](uninstalling.md) — there is no uninstaller script yet, so the folders are listed
there.

**How do I get help?**
Ask Bakunawa in the app first; he knows your specific install. Otherwise **support@siklabcore.com**,
target two business days, Philippine time. Never send keys, passwords or customer data.
