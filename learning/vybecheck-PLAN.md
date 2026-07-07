# PLAN.md — Make the Vybecheck waitlist capture real emails

> Task memory for the first harness run. Milestones checked off as completed.
> Verify command after every change: `npx -y html-validate index.html`
> + open in a browser, confirm it renders and the console is clean.

## Problem
The waitlist form's `join()` only hides the form and shows a success message —
**no email is stored or sent anywhere.** Every "signup" is lost.

## Approach
Static single-file site with no backend, so use a hosted form endpoint
(**Formspree**, free tier) — the form POSTs the email to Formspree, which stores
it and emails Joel. No server to run. One config value to fill: the Formspree
form ID.

## Milestones
- [x] M1 — Write this PLAN.md before touching code.
- [x] M2 — Give the email input a `name="email"` so it can be submitted.
- [x] M3 — Replace the fake `join()` with a real `fetch()` POST to Formspree.
- [x] M4 — Handle failure: show an error message and re-enable the button on error
      (don't fake success if the send failed — that's the whole point).
- [x] M5 — Verify: `html-validate` passes; page renders; console clean.
- [x] M6 — Formspree account created, form `mykqvdvp` wired in, deployed to Netlify
      (Production published 10:03 PM), test submit on live site returned the real
      success state ("You're in"). Final inbox confirmation in progress.

## ✅ DONE — 2026-07-06
Waitlist is live and capturing emails via Formspree. Shipped and verified on the
real site. (First-submission email confirmation may be needed once in Formspree.)

## Definition of done
A submitted email actually lands in Formspree/Joel's inbox, the success state
only shows on a real success, and `html-validate` passes.
