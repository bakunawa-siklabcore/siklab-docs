# Getting Started

Siklab Core installs as a single app on your own machine and runs in your browser. Setup takes a couple of minutes.

---

## What you'll need

- **A computer to run it on** — Siklab installs as one self-contained app; there's nothing else to set up.
- **An AI engine** — Siklab uses an AI model to do the work. If you already have an AI coding assistant installed on your machine, Siklab finds it and uses it, and you're signed in through that tool as usual — no separate key to buy or manage. A hosted provider's API key is an alternative, not a requirement.

---

## Install & first run

1. **Install Siklab Core** using the installer you were provided.
2. **Open the address it prints** in your browser (it runs locally on your machine).
3. **Set a password.** On first launch you choose an owner password — this is how you sign in from then on.
4. **Check your engine.** On a first run Siklab looks for AI assistants already on your machine and switches on what it finds, so there is usually nothing to do here. Settings → **Engines** shows what it found.

That's it — you're ready to build.

---

## Create your first app

1. On the **Start** screen, choose **Build an app**.
2. Describe what you want in your own words — for example, _"a simple habit tracker where I check off tasks each day."_ Siklab helps you tighten the request as you go.
3. **Review the plan** Siklab restates back to you, and approve it.
4. **Refine the preview.** You'll get an interactive preview you can click through. If something's off, just say so — _"make the buttons bigger,"_ _"add a weekly total"_ — and it updates.
5. When it looks right, choose **Build it for real**. Siklab builds the finished app and hands it back with a short guide.

Your finished apps live on the **Files** page, where you can open and keep them.

!!! note "If you asked for something without a screen"
    A command-line tool, a script or a small library has no preview to click and no page to open.
    For those, Siklab skips step 4 and goes straight to building — then **runs** what it made to
    check it works, and tells you what it produced and where. You'll get the code and a note on how
    to run it, rather than a page on the Files list.

---

## Choosing what powers your agents

Everything lives in Settings → **Engines**.

**Active vs available.** Each tool Siklab knows about is either **Active** — offered to your agents —
or **Available**, meaning it's on your machine but sitting unused until you say so. A first run turns
on what it finds; anything you install *later* arrives as Available, so switching it on is your call
rather than a surprise. Use **Activate** or **Deactivate** on any row.

**Give one agent a different tool.** Under *Per-agent engine*, each of your agents can run on
whichever engine you prefer. Leave them on the default unless you have a reason.

**Find more.** **Find more CLIs** looks beyond the tools Siklab ships support for and lists anything
on your machine that looks like an AI assistant. Nothing is switched on by the search — you get a
list and decide. Adding one puts it in your channels as Available.

**Set it up for you.** For a tool Siklab doesn't already know how to drive, **Set up for me** asks
your main AI assistant to work out the right settings, then *tests them before trusting them* — the
tool has to correctly answer a question only that test knows. If it passes, the tool is configured
and switched on. If it doesn't, Siklab tells you what happened, keeps the suggested settings so you
can correct them, and leaves the tool off. Anything you typed yourself is never overwritten.

**Using a hosted provider instead.** If you'd rather use an API key, **+ Add an API connection**
under *Connections* takes one. Keys are stored encrypted on your machine.

---

## Keeping it running

- **Sign in** with your owner password each time you open Siklab.
- **Updates** are delivered in-app — when a new version is available, you'll be prompted, and updating is one click.
- **Add more later.** Come back any time to add a feature, fix a problem, or plan your next project — all in the same place.

---

!!! note
    Step-by-step guides for each part of Siklab are on the way and will appear here as they're published.
