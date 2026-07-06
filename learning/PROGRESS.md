# PROGRESS.md — Your Harness Engineering journey

> Personal tracker for the **Harness Engineering: Zero to Hero** field manual
> (github.com/Fade2Paid/harness-starter-pack). Started **2026-07-06**.
>
> **The rule: a box gets checked only when it's true for YOU.** No inherited
> checkmarks, no faking mastery. Honesty here is the whole point — the tracker
> is only useful if it reflects what you can actually do.

---

## Where you're starting (and why not from zero)

You've already built **2 websites and an app with Claude**, and you're
comfortable with **Terminal + PowerShell**. That means you've *lived* the
early levels without naming them. So:

- **Level 0–1:** mostly credited — you've run an agent framework end to end and
  made model calls in a loop. You just haven't named the parts yet.
- **Level 2:** where your real learning begins. You've *used* tools, context,
  and permissions; now you learn to *name and design* them.
- **Level 3:** your first real goal — build a harness on purpose, not by vibes.

---

## ▶ START HERE — your next 3 actions

1. **Read** the field manual's Level 0–2 pages (the "Zero to Hero" PDF).
2. **Write your own one-paragraph definition of "harness"** in the Level 0
   READ box below. In your own words — that's how you know it's yours.
3. **Pick the ONE project** you'll turn into your first real harness (a website
   or the app) and name its **verify command** (e.g. `npm test`, `npm run build`).

Do those three and you're standing on Level 3's doorstep.

---

## ▣ Level 0 — Orientation

**READ**
- [x] Read the Orientation + Mental Model pages — walked through the field manual (pp.1–3).
- [x] Write your own one-paragraph definition of "harness."
  > _Joel's definition (2026-07-06):_ "A codebase for agents that acts like laws
  > the agent obeys — so it doesn't trust itself to act, but verifies its actions
  > are the correct steps."
- [x] Draw the loop (observe → plan → act → verify) — you learned it this session.

**BUILD**
- [ ] Pick the task your first harness will tackle (one concrete, verifiable thing).
- [x] Pick your stack: **Claude + Claude Code** (Claude Agent SDK family).
- [x] Pick your first-harness project: **Vybecheck** (vybecheck.app).

**Exit:** you can explain what a harness is and why every component is temporary.

---

## ▣ Level 1 — Foundations

**READ** — covered via the field manual's Foundations synthesis (p.4); originals
linked in the manual for a deeper dive later.
- [x] Both *Harness Engineering* essays (OpenAI + Fowler) — 3 systems; "humans on the loop."
- [x] *Building Effective Agents* (Anthropic) — workflow vs. agent; compose primitives.
- [x] *Harness Design for Long-Running Application Development* — "assumptions expire."
- [x] *The Anatomy of an Agent Harness* (LangChain) — the 5 primitives.
- [x] Skim *Writing Effective Tools* / *Beyond Permission Prompts* / *Demystifying Evals*.

**BUILD**
- [x] Install a framework and run its quickstart E2E — done: you built real apps.
- [x] Confirm you can make one successful model call inside a loop — done.

**Exit:** you can name the 4 loop steps, 5 primitives, and why assumptions expire.

---

## ▢ Level 2 — Design Primitives  ← YOU ARE HERE

**READ** — one pass per primitive
- [x] Agent Loop — saw it live in gclaw's heartbeat (SKILL.md:63).
- [x] Planning — gclaw's numbered procedure + forge.py ranked intents.
- [x] Context — gclaw loads references on-demand; summaries to context, full logs to file.
- [x] Tool Design — gclaw's `open_perp_position` strict schema (SKILL.md:96).
- [x] Skills & MCP — gclaw IS a skill on the GDEX MCP; forge writes its own.
- [x] Permissions — gclaw's "deterministic, never advisory" riskguard + deny-list.
- [x] Memory — gclaw's metabolism.json + regime-conditional memory.py.
- [ ] Skim: Orchestration, Verification, Observability, Debugging, HITL.

**BUILD**
- [ ] Define 3–5 tools with clear names + strict schemas.
- [ ] Add structured-output enforcement (no ad-hoc JSON parsing).
- [ ] Turn on prompt caching for system prompt + tool defs.

**Exit:** all 12 primitives named, each mapped to a loop stage, framework run E2E.

---

## ▢ Level 3 — Build Your First Harness

**READ**
- [ ] Work through *Learn Harness Engineering* (or shareAI-lab/learn-claude-code).
- [ ] Read smolagents or rasbt/mini-coding-agent core, front to back.
- [ ] Read *Skill Issue: Harness Engineering for Coding Agents*.

**BUILD — the "Hello, Harness" milestone**
- [ ] Loop runs observe → plan → act → verify.
- [ ] Writes a `PLAN.md` and updates it each turn.
- [ ] Destructive tools gated behind a permission check.
- [ ] Runs a test after every change; feeds **only summary lines** back to context.
- [ ] Logs full output to a file, not the context window.

**Exit:** a single-agent harness completes your Level 0 task on its own.

---

## ▢ Level 4 — Scale & Orchestrate

**READ**
- [ ] *Choosing the Right Multi-Agent Architecture*.
- [ ] *Effective Harnesses for Long-Running Agents*.
- [ ] The protocol map (MCP / A2A / AG-UI).

**BUILD**
- [ ] Add a sandbox (E2B or Daytona) for code execution.
- [ ] Add a second specialized agent **only if** isolation/parallelism earns it.
- [ ] Add checkpoint-resume so a long task survives a restart.

**Exit:** harness handles a task bigger than one context window without losing progress.

---

## ▢ Level 5 — Harden, Verify, Observe

**READ**
- [ ] *Demystifying Evals* + *Agent Evaluation Readiness Checklist*.
- [ ] *How We Contain Claude* + OWASP LLM01 (prompt injection).
- [ ] Skim a sandbox option (E2B / Daytona / NVIDIA OpenShell).

**BUILD**
- [ ] Add promptfoo CI evals — capability evals separate from regression evals.
- [ ] Add tracing (Langfuse or OpenLLMetry) on every inference + tool call.
- [ ] Run the lethal-trifecta check; lock hooks/MCP config from agent edits.

**Exit:** a regression is caught by CI before it ships; every step is traceable.

---

## ▢ Level 6 — Ship to Production

**READ**
- [ ] *State of Agent Engineering 2026* (mind the eval gap).
- [ ] *FinOps for Agents* + a cost-optimization guide.
- [ ] *Backtesting AI Agents* (pass^k).

**BUILD**
- [ ] Gateway budget caps: loop/step limits, tool-call caps, token + wall-clock limits.
- [ ] Backtest with pass^k (dataset: 20% golden / 30% edge / 20% adversarial / 30% regression).
- [ ] Wire a self-heal path: detect regression → attribute → open fix PR.

**Exit:** harness runs unattended within budget and recovers from its own failures.

---

## ▢ Final — Hero Gate

- [ ] Walk every item in `HARNESS_CHECKLIST.md`; no honest box left unchecked.
- [ ] Copy + customize all four starter files (`AGENTS.md`, `PLAN.md`, `IMPLEMENT.md`, `HARNESS_CHECKLIST.md`).
- [ ] For every component, ask: *what is this assuming the model can't do?* Delete the crutches it no longer needs.
- [ ] **Ship it.**

---

### Scorecard
| Level | Read | Build | Exit met |
|-------|------|-------|----------|
| 0 — Orientation | ☐ | ☐ | ☐ |
| 1 — Foundations | ☑ | ☑ | ☑ |
| 2 — Primitives  | ☐ | ☐ | ☐ |
| 3 — Build       | ☐ | ☐ | ☐ |
| 4 — Scale       | ☐ | ☐ | ☐ |
| 5 — Harden      | ☐ | ☐ | ☐ |
| 6 — Ship        | ☐ | ☐ | ☐ |
| Hero Gate       | — | — | ☐ |

> The best harness is the smallest one that still works.

---

### Session log
_A short note each session — what you learned, what's next. Newest on top._

- **2026-07-06 (7)** — Joel wrote his own definition of "harness" (recorded in
  the L0 READ box) — strong grasp of the verification + "laws the agent obeys"
  core. One L0 box left: pick the first concrete harness task.
- **2026-07-06 (6)** — Walked the field manual's Level 1 Foundations (p.4):
  Fowler's 3 systems + "humans on the loop," workflow-vs-agent, "assumptions
  expire," the 5 primitives, the PLAN/IMPLEMENT/Documentation artifact pattern
  (= the starter-pack files), and the constitutive 4-element definition of a
  harness. **Level 1 closed** — exit criterion met (name loop steps, primitives,
  why assumptions expire). Next: Level 2 primitives in the manual (already did
  the 7 core via gclaw; will cover the remaining orchestration/verify/observe/HITL).
- **2026-07-06 (5)** — Got the REAL Vybecheck codebase: a single static
  `index.html` (plain HTML/CSS/JS, no framework/npm/build) — my Next.js guess
  was wrong. Rewrote `vybecheck-AGENTS.md` for the true stack; verify is now
  `npx html-validate index.html` + browser console check. Live proof of the
  manual's "verify, don't assume" lesson. Candidate first tasks noted: the
  waitlist form doesn't save emails; pricing buttons have no action.
- **2026-07-06 (4)** — Started reading the field manual together. Covered
  Section 0 (Orientation) + the Mental Model (pp.1–3): the definition, the core
  "every crutch is temporary" principle, the 5 primitives, the observe→plan→act
  →verify loop + reasoning sandwich, and the rank-30→top-5 lesson. Checked the
  L0 "read Orientation + Mental Model" box. Next: Level 1 Foundations (p.4).
- **2026-07-06 (3)** — Picked Vybecheck as the first-harness project. Drafted its
  `AGENTS.md` (learning/vybecheck-AGENTS.md) assuming a Next.js/React + npm stack.
  Open: confirm the stack via `cat package.json` and fix the ⚠ lines; write PLAN.md.
- **2026-07-06 (2)** — Walked the 7 Level-2 primitives using gclaw's real code
  as the example, and mapped each to a loop stage. Checked the 7 primitive READ
  boxes. Wrote `learning/AGENTS.template.md` (fill-in, with gclaw as the worked
  example). Remaining for L2: skim orchestration/verification/observability/HITL,
  then the 3 BUILD tasks. Next action for you: pick your first-harness project +
  its verify command, then fill in the template.
- **2026-07-06 (1)** — Set up the tracker. Established the mental model (observe →
  plan → act → verify + the 5 primitives). Credited Level 1 BUILD from your
  prior app work.
