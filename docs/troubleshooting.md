# Troubleshooting

Start here when something is wrong. The page is ordered by how often each thing actually happens.

**Before anything else: ask Bakunawa**, bottom right of the app. He knows your version, your trial,
which engine you are on, and where your work is — which is most of what this page has to guess at.

---

## A build looks stuck, or stops for no reason

**This is the most common problem, and it is usually not Siklab.** Some AI engines throw provider
errors far more often than others. From the outside that looks identical to a hang.

What to do, in order:

1. **Check which engine that agent is on** — Settings → Engines.
2. **If it is on `agy`, `opencode` or `qwen`, switch to `claude` or `codex`** and run it again. See
   [Known Issues](known-issues.md) for why those three are singled out.
3. **If it stops again on a recommended engine**, check that the engine works on its own: open a
   terminal and run the CLI directly. If it fails there, it is not Siklab — sign in again or check
   your provider's status page.
4. **Check your allowance.** Free and trial tiers run out. A full build can be hundreds of model
   calls, so an allowance that looks generous can disappear inside one project.

Partial work is kept. A build that stops does not throw away files already written — pick it up
rather than starting over.

---

## "No AI engine connected"

Siklab contains no AI model and no API key. It drives a CLI you installed, or an API key you
supplied. That banner means it can find neither.

- **You have a CLI installed but Siklab does not see it.** Settings → Engines → **Find more CLIs**.
  It scans for anything that looks like an AI assistant. Nothing is switched on by the search — you
  get a list and decide.
- **You installed a CLI after first run.** It arrives as *Available*, not *Active*, on purpose.
  Press **Activate**.
- **You have no CLI at all.** Use an API key instead: Settings → Engines → **+ Add an API
  connection**. Anthropic-, OpenAI- and Google-shaped endpoints all work.

---

## I can't sign in / I forgot my password

There is no password reset email, because there is no account and no server holding your identity.
Recovery is local and deliberate:

```bash
cd ~/.siklab-core && ./siklab-api-<platform> recover
```

It prints a one-time key valid for 15 minutes. Replace `<platform>` with the binary name in that
folder.

---

## The app won't start

**On any platform** — check nothing else is already using the port. Siklab opens at
`http://localhost:3200`.

**On Linux or WSL, with a message about AVX2** — the CPU does not support an instruction set the
runtime needs. This is a hard requirement, not a setting; the launcher refuses with a named error
rather than crashing later. There is no workaround on that machine.

**On WSL after a reboot** — WSL has no systemd by default, so nothing restarts Siklab for you. Start
it again from your WSL terminal.

**On Linux or WSL, when verification steps fail but building works** — the browser-backed checks
need Chromium system libraries. Siklab installs them where it has permission, and prints the exact
command when it does not. Run that command.

---

## The database is corrupted

Almost always one cause: **the data directory is on a Windows drive mounted into WSL** (`/mnt/c/…`).
SQLite's journaling is not safe across that mount type, and the file gets damaged.

Keep `~/.siklab` on the Linux filesystem, not on `/mnt/…`. Siklab detects the risky mount types it
can and steps down to a safer journal mode, but the mount is still the wrong place for a database.

If a database is already damaged, Siklab prints a recovery recipe before you delete anything. Follow
it — you can usually get the data back.

---

## The app it built is wrong

Not a bug report — just tell Mayari, in the same plain words you would use with a colleague:

> The total is wrong when I delete a row.

> I wanted a monthly view, not weekly.

She sends it back and returns with a new version. You do not need to work out whether that counts as
a bug or a new feature.

---

## "Couldn't be confirmed" in a delivery

That is not "it's broken". It means the test did not complete, so **nobody verified it** — treat it
as unknown and try that part yourself.

**Checked** means Sidapa opened the app in a real browser and tried that exact thing, with a saved
record. Checked is still not the same as correct: verification covers the flows it was asked to
cover. It is not proof the app has no bugs, and it is not a security review.

---

## Updates won't install

Updates need a valid licence. If yours has lapsed the app keeps running and your work stays yours,
but new versions are held back until it renews.

If the app says it cannot reach the update source, that is a network result, not a verdict about
your version — it does not mean you are up to date.

---

## Still stuck

**support@siklabcore.com**, within 2 business days, Philippine time. Siklab Core is run by one
person; that is a goal, not a contract.

You can also **Report a problem** from the top bar. It attaches your version, your OS, and an
optional screenshot.

!!! danger "Never send secrets"
    Do not put API keys, passwords, licence keys, private keys or customer data in a report or an
    email. Reports are not automatically redacted, and no one at Siklab will ever ask you for any of
    those.
