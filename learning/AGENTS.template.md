# AGENTS.md — fill-in template (with gclaw as the worked example)

> Copy this into the ROOT of YOUR project (a website or the app), delete the
> `>` annotation lines, and fill the blanks. Keep it SHORT and HIGH-SIGNAL:
> only rules that would cause a bug if the agent forgot them mid-task.
>
> Each section shows how **gclaw** (this repo) answers it, so you have a real
> example next to every blank.

---

## 1. What this project is
> gclaw's answer: "A Claude Code skill that runs a living trading agent on the
> GDEX MCP; Python + Node; done = heartbeat runs a full safe trade cycle."

- **Product:** ______
- **Primary language / runtime:** ______
- **Package manager:** ______
- **Where the entrypoint lives:** ______

## 2. How to work here (the loop)
> Keep this section AS-IS — it's the universal observe→plan→act→verify cycle.

1. **Read** `PLAN.md` (if present) before doing anything. If absent, create one.
2. **Plan** — write/update milestones in `PLAN.md` before writing code.
3. **Act** — make the smallest change that advances the current milestone.
4. **Verify** — run the verification command below after every change.
5. **Record** — append decisions and deviations to `IMPLEMENT.md`.
6. Repeat until all milestones are `[x]`.

## 3. Commands
> gclaw's verify is `uv run --no-project ruff check scripts/` + node --check.
> YOURS is whatever proves your app still works — the ONE line that matters most.

| Action            | Command   |
|-------------------|-----------|
| Install deps      | ______    |
| Run / dev server  | ______    |
| **Verify (tests)**| ______  ← run after every change |
| Lint / format     | ______    |
| Typecheck         | ______    |
| Build             | ______    |

## 4. Conventions
> gclaw's: "≤100 lines/function, absolute imports; replace don't deprecate;
> commit subjects imperative ≤72 chars; do NOT touch lockfiles."

- **Code style:** ______
- **Naming:** ______
- **File layout / where things go:** ______
- **Tests live in:** ______
- **Commit message format:** ______
- **Do NOT touch:** ______

## 5. Tool & permission boundaries
> gclaw's lesson: "Safety is deterministic, never advisory." The dangerous
> stuff is blocked in CODE, not by asking. Yours can be lighter, but name it.

- **Allowed without asking:** read files, run tests, lint, typecheck, search.
- **Ask first:** deleting files, schema/migration changes, editing CI, anything
  touching secrets/auth, network calls, installing new dependencies.
- **Never:** commit secrets, force-push, edit this file to widen its own
  permissions, or disable verification.

## 6. Definition of done
- [ ] All `PLAN.md` milestones checked off.
- [ ] The verify command passes cleanly.
- [ ] Lint + typecheck pass.
- [ ] No debug code, no commented-out blocks, no leftover TODOs.
- [ ] `IMPLEMENT.md` records what changed and any open questions.

---
> Maintainer note: when the agent repeats a mistake, that mistake is a missing
> line HERE. Add it. And delete any rule the model now handles on its own —
> every line is a temporary crutch.
