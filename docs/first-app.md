# Your First App

A walkthrough of one build, start to finish, with the decisions you make and roughly what to
expect at each. Fifteen minutes for something small.

If you have not installed yet, start with [Getting Started](getting-started.md). If you are not
sure your machine qualifies, [Requirements](requirements.md) is the honest list.

---

## Pick something small and real

The best first build is something you actually want and can describe in a sentence. A habit
tracker. An invoice log. A reading list with ratings.

Two things make a first build go badly, and both are avoidable:

- **Too vague.** *"A productivity app"* has no screens in it, so the first thing that happens is
  a long series of questions.
- **Too large.** *"A CRM with billing, email and a mobile app"* is four projects. You will get
  further asking for the first one and adding to it.

You are not locked in. Ask for the reading list, then add ratings, then add a monthly view. Adding
to something that works is the easiest kind of change.

---

## 1. Describe it

On **Start**, choose **Build an app** and say what you want in plain words. No format, no
technical vocabulary, no bullet lists required:

> A reading list where I add books, mark them finished, and give them a rating out of five.

**Mayari** reads it and comes back with questions. She will ask things like whether ratings are
required, whether you want the date you finished, what happens to a book you abandon.

**Answer them properly — this is the highest-leverage part of the whole process.** She is not
stalling. A brief that is wrong in scope produces an app that is wrong everywhere, and the
questions are how that gets caught while it still costs nothing. "I don't mind, you choose" is a
fine answer when you genuinely don't mind.

When she has enough, she restates what she is going to build. Read it. If it is off, say so now.

---

## 2. Approve the design

**Tala** produces a clickable mockup — a real page in your browser, not a picture of one. Click
through it.

Say what is wrong in ordinary language: *"the rating should be stars, not a number"*, *"put
finished books in their own section"*, *"this is too cramped"*. It comes back changed.

**Nothing is built until you approve this**, and that is deliberate. Changing your mind here is
free. Changing it after the build costs a rebuild.

---

## 3. It gets built and checked

Approve, and **Apolaki** writes the actual application against the design you signed off.

Then **Sidapa** opens it in a real browser and clicks through it — adds a book, marks it finished,
sets a rating. When something fails, the work goes back for repair rather than forward to you.

This is the long part. A small app is minutes; something with several screens takes longer. You do
not need to watch it.

!!! warning "If it looks stuck"
    A build that stalls or stops for no visible reason is usually the AI engine, not Siklab. Some
    engines throw provider errors far more often than others — see the known-unstable list in
    [Requirements](requirements.md). Switch to a recommended engine in **Settings → Engines** and
    try again before assuming the product is broken.

---

## 4. Take delivery

**Yagu** hands it over with an account of what was checked — and, just as importantly, what could
not be confirmed.

Read that part. **Checked** means Sidapa opened the app and tried that exact thing, with a saved
record. **Couldn't be confirmed** means the test did not complete — not that it is broken, but
that nobody verified it, so try it yourself.

Checked is not the same as correct. Verification covers the flows it was asked to cover. It is not
proof the app has no bugs, and it is not a security review. Review anything you are going to rely
on.

Your app is on the **Files** page, and on disk in an ordinary folder you can open in any editor.

!!! note "If you asked for something with no screen"
    A script, a command-line tool or a small library has nothing to click. Siklab skips the mockup
    step, builds it, then **runs** it to check it works, and tells you what it produced and how to
    run it.

---

## 5. Change it

Tell Mayari what is wrong or what you want next, in the same plain words:

> The total is wrong when I delete a book.

> I want to see how many I finished each month.

She sends it back and returns with a new version. You do not need to work out whether that is a bug
or a feature — just say what is wrong.

---

## What you get to keep

You own what the factory produces for you. The applications Siklab builds — source, assets,
documentation, **including anything built during the trial** — are yours to use, change, host and
sell. No royalty, no attribution, and none of Siklab's code is inside them.

Generated projects usually pull in third-party libraries under their own licences. Siklab cannot
grant rights it does not have, so check those before shipping commercially.

---

## Where to go next

- **[Requirements](requirements.md)** — platforms, engines, and the current known limitations
- **[How the Forge Works](how-the-forge-works.md)** — the whole model in one page
- **Ask Bakunawa**, bottom right of the app. He knows your version, your trial, and where your work
  is. He is the right first stop for almost anything.
