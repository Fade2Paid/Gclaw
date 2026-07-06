# AGENTS.md — Vybecheck

> Operating rules for any AI agent working on Vybecheck. Copy this file into the
> project root (`~/vybecheck-web/`, next to `index.html`). Keep it short and
> high-signal: only rules that would cause a bug if the agent forgot them.

---

## 1. What this project is

- **Product:** VybeCheck (vybecheck.app) — a marketing landing page for a
  "swipe app for the creator economy." Hero, six audience cards, how-it-works,
  pricing, and an email waitlist form.
- **Type:** Static single-page website. **One file: `index.html`.**
- **Language / runtime:** Plain HTML + CSS + vanilla JavaScript. **No framework.**
- **Package manager / build:** **None.** No `package.json`, no build step. The
  file runs directly in a browser.
- **Entrypoint:** `index.html` (CSS is inline in `<style>`, JS inline in `<script>`).

## 2. How to work here (the loop)

1. **Read** `PLAN.md` (if present) before doing anything. If absent, create one.
2. **Plan** — write/update milestones in `PLAN.md` before editing.
3. **Act** — make the smallest change that advances the current milestone.
4. **Verify** — run the verify check below after every change.
5. **Record** — append decisions and deviations to `IMPLEMENT.md`.
6. Repeat until all milestones are `[x]`.

## 3. Commands / verification

There is no build or test suite. "Does it still work?" is checked two ways:

| Action              | How                                                        |
|---------------------|-----------------------------------------------------------|
| **Verify (structure)** | `npx -y html-validate index.html`  ← run after every change |
| **Verify (visual)**    | Open `index.html` in a browser; confirm it renders and the console (Cmd+Option+J) shows **no red errors**. |
| Format (optional)   | `npx -y prettier --write index.html`                      |

> A change isn't done until the page still renders correctly AND the console is
> clean. Because it's one file, a single broken tag can blank the whole page —
> so verify every time.

## 4. Conventions

- **Single-file by design.** Keep HTML, CSS, and JS in `index.html` unless we
  explicitly decide to split them. Don't introduce a framework or build step
  without asking.
- **Colors:** use the CSS variables in `:root` (`--coral`, `--cyan`, etc.).
  Don't hard-code new hex values — add a variable if a new color is needed.
- **Style:** match the existing 2-space indentation and class-naming pattern.
- **Commit format:** short imperative subject (e.g. "Fix waitlist form submit").
- **Do NOT touch:** don't add tracking scripts, external CDNs, or dependencies
  without asking (it's a fast, self-contained page — keep it that way).

## 5. Tool & permission boundaries

- **Allowed without asking:** read the file, edit copy/styles/layout, run the
  validator, open in a browser.
- **Ask first:** adding a real backend or form handler, adding dependencies or a
  build step, adding third-party scripts (analytics, chat, pixels), changing the
  domain/deploy setup, or anything that sends user data anywhere.
- **Never:** commit secrets/API keys, add hidden trackers, or wire the waitlist
  to a service without explicit approval (it collects email addresses).

## 6. Definition of done

- [ ] All `PLAN.md` milestones checked off.
- [ ] `npx html-validate index.html` passes.
- [ ] Page renders correctly in a browser; console has no errors.
- [ ] No leftover debug code or commented-out blocks.
- [ ] `IMPLEMENT.md` records what changed and any open questions.

---
> ⚠ Known gaps in the current code (candidate first tasks — see notes to Joel):
> the waitlist form doesn't actually save emails (it only hides itself), and the
> pricing buttons have no action yet.
