# Uninstalling

**There is no uninstaller script yet.** Rather than pretend otherwise, here is exactly what is on
your machine and what removing each thing costs you.

---

## Take your work out first

Everything Siklab built for you is yours, and removing the app does not take it with it — but it
does live under a folder you are about to delete. **Copy anything you want to keep before you start.**

| What | Where |
|---|---|
| Your projects and generated apps | `~/.siklab/workspaces/` |
| Mockups and delivered artefacts | `~/.siklab/vault/studio/` |

These are ordinary folders. Copy them anywhere; they need no Siklab component to open or to run.

---

## Remove the app

```bash
rm -rf ~/.siklab-core
```

That is the application itself — the binary, the interface, and the launcher.

---

## Remove your data

```bash
rm -rf ~/.siklab
```

This is irreversible. It removes your projects, your database, your settings, your encrypted
credentials and your licence state. **Make sure you copied your work out first.**

---

## Remove the entitlement record

```bash
rm -f ~/.siklab/.entitlement
```

Covered by the previous step if you removed `~/.siklab` entirely. It is listed separately because it
sits deliberately outside the data folder, so that clearing data does not silently restart a trial.

---

## If you started it automatically

If you set Siklab to start on login, remove that too — it is not created by the installer, so it
only exists if you added it.

- **macOS** — a `launchd` plist in `~/Library/LaunchAgents/` if you made one.
- **Linux with systemd** — a unit you added, usually under `~/.config/systemd/user/`.
- **WSL** — WSL has no systemd by default, so there is usually nothing here.

---

## Your subscription is separate

**Removing the app does not cancel your plan.** Billing is handled by Paddle, and cancelling is done
through the link in your purchase receipt or by emailing **support@siklabcore.com**.

Cancel before your next renewal date if you do not want to be charged again. See
[Cancellation & Refunds](https://siklabcore.com/refunds).

---

## What is not on your machine

Nothing to clean up on our side — there is no account to close and no server holding your projects.
The only records that exist are your licence activation and any problem reports you chose to send.

If you want those removed, email **support@siklabcore.com** and say so.

---

Reinstalling later is the normal install command; your licence still works, on the same terms.
