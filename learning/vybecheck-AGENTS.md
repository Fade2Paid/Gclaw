# AGENTS.md — Vybecheck

> Operating rules for any AI agent working on Vybecheck. Copy this file into the
> ROOT of the Vybecheck project on your Mac (next to package.json), then confirm
> the two ⚠ lines below. Keep this file short and high-signal.
>
> ⚠ = a best-guess I made from the typical Claude-built Next.js app. Run
> `cat package.json` in the project and check the "scripts" section; fix any ⚠
> line that doesn't match.

---

## 1. What this project is

- **Product:** Vybecheck (vybecheck.app) — a web app built with Claude.
- **Primary language / runtime:** TypeScript/JavaScript on Node.js ⚠ (confirm)
- **Framework:** Next.js / React ⚠ (confirm)
- **Package manager:** npm ⚠ (confirm — pnpm/yarn if you see a pnpm-lock.yaml/yarn.lock)
- **Where the entrypoint lives:** `app/` or `pages/` directory ⚠

## 2. How to work here (the loop)

The agent must follow this cycle on every task:

1. **Read** `PLAN.md` (if present) before doing anything. If absent, create one.
2. **Plan** — write/update milestones in `PLAN.md` before writing code.
3. **Act** — make the smallest change that advances the current milestone.
4. **Verify** — run the verify command below after every change.
5. **Record** — append decisions and deviations to `IMPLEMENT.md`.
6. Repeat until all milestones are `[x]`.

## 3. Commands

| Action             | Command            |
|--------------------|--------------------|
| Install deps       | `npm install`      |
| Run / dev server   | `npm run dev`      |
| **Verify (build)** | `npm run build`  ← run after every change ⚠ |
| Lint / format      | `npm run lint` ⚠   |
| Typecheck          | `npx tsc --noEmit` ⚠ (only if it's TypeScript) |

> **Verify is mandatory.** A change isn't done until `npm run build` passes.
> If you add real tests later, the test command becomes the verify command.

## 4. Conventions

- **Code style:** match the existing files — don't reformat untouched code.
- **File layout:** put new components/pages where the existing ones live.
- **Commit message format:** short, imperative subject (e.g. "Add pricing page").
- **Do NOT touch:** `package-lock.json`, `node_modules/`, `.next/`, `.env*` files.

## 5. Tool & permission boundaries

- **Allowed without asking:** read files, run the dev server, build, lint, search.
- **Ask first:** deleting files, changing anything in `.env` / secrets / API keys,
  installing new dependencies, editing deploy/CI config, changing auth or the
  database schema.
- **Never:** commit secrets or `.env` files, force-push, disable the build check,
  or edit this file to widen its own permissions.

## 6. Definition of done

- [ ] All `PLAN.md` milestones checked off.
- [ ] `npm run build` passes cleanly.
- [ ] Lint passes (and typecheck, if TypeScript).
- [ ] No leftover debug code, commented-out blocks, or TODOs for this task.
- [ ] `IMPLEMENT.md` records what changed and any open questions.

---
> When the agent repeats a mistake, add a line here that would have prevented it.
> Delete any rule the model now handles reliably on its own.
