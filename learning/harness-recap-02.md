# Harness Engineering — Recap #2: Verification

> Your plain-language recap of Lever 3. Re-read anytime. Cover the quiz answers
> at the bottom and say them out loud. (See Recap #1 for Levers 1 & 2.)

---

## The problem it solves

Your frustration: *"Claude changed something and broke another part."*

**Claude cannot reliably tell if its own work is correct just by looking at it.**
It finishes a change, genuinely *believes* it's fine, and moves on — while
something two files over is now broken. Its confidence is not proof.

Chef version: a chef tasting its *own* cooking mid-service can be fooled. You
don't *ask* the chef "is it good?" — you **taste it** yourself. The taste is
objective; the chef's opinion isn't.

---

## Lever 3 — Verification

**Verification = an external check that *proves* the work actually works** — a
real test you run that gives an honest pass/fail, not Claude's opinion.

The rule of the whole lever, in three words:

> **Don't trust — verify.**

**The verify command** is the practical form: one command that objectively
answers "does it still work?"

- Website → `npx html-validate index.html`, or load the page and check the
  console, or `npm run build`.
- Code with tests → `npm test`, `pytest`.

Run it **after every change**, and nothing is "done" until it **passes**.

*(This is why the Vybecheck edits — 11 of them — never shipped a broken one.
Every change was verified before it counted.)*

---

## The two things that finish the lever

1. **The verify command is the single most important line in `AGENTS.md`.**
   The starter pack says it plainly: *"that one line does most of the work."*
   Everything else is polish; the taster is the engine.

2. **"Not done until it passes" is part of your definition of done.** A change
   is finished when the check *proves* it, not when Claude *says* it.

And it locks into Lever 1: the verify rule only works if it's **pinned in
`AGENTS.md`**, so Claude can't skip it. The levers combine — they aren't
separate boxes.

---

## Not everything is checkable by a command

Some work is **objective** (a command can check it). Some is **subjective**
(only a human can judge it). Verification splits accordingly:

| Kind | Who tastes it | Example (your video pipeline) |
|---|---|---|
| **Objective** | a command (Claude runs it) | right length, right aspect ratio, not a duplicate you rejected |
| **Subjective** | **you** (the human) | does it look good? does it match your style? |

Your **approval gate is verification** for the creative part — *you* are the
taster. That's the "human on the loop" again: automate the objective checks,
keep the taste test for yourself.

---

## Quiz yourself (cover the answers)

1. Why can't you just trust Claude when it says "that worked"?
2. What is a "verify command," in one sentence?
3. When should the verify command run, and when is a change "done"?
4. Which single line in `AGENTS.md` does most of the work?
5. For a generated video: name one check a command can do, and one that needs
   you.
6. Which earlier lever does verification depend on, and why?

<details>
<summary>Answers</summary>

1. Claude can't taste its own work — its self-assessment is a guess, and it can
   be confidently wrong.
2. One command that objectively answers "does it still work?" with a pass/fail.
3. After **every** change; the change is done only when the check **passes**.
4. The verify command.
5. Command: length / aspect ratio / duplicate check. You: does it look right /
   match my style.
6. Lever 1 (context) — the verify rule must be **pinned in `AGENTS.md`** so
   Claude can't forget to run it.

</details>

---

## Where you are

Three levers, solid: **Context (the desk)**, **Tools (MCP)**, **Verification**
— plus Planning and Permissions from your fal.ai gate. That's the core of
harness engineering, and you can apply all of it to a real project.

*Next: turn it into your actual YouTube/fal.ai `AGENTS.md`.*
