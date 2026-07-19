# Harness Engineering — Recap #1: The Desk & The Tools

> Your plain-language recap of Levers 1 and 2. Re-read it anytime. The quiz at
> the bottom is the point — cover the answers and try to say them out loud.

---

## The one big idea

There are **two separate things**:

- **The model (Claude)** = a brilliant chef with amnesia in an empty, dark room.
  Pure skill, but no memory, no hands. On its own it can only produce text.
- **The harness** = everything *you* set up around the model so it works
  reliably: what it sees, what it can do, what it remembers, what it's allowed
  to do, and how it checks itself.

**Your prompt is part of the harness** — it's the "what the model sees" part.
So better prompting = better harness management, not magic words.

Everything runs on one loop: **observe → plan → act → verify → repeat.**

---

## Lever 1 — Context (the desk)

Claude has a **desk** that only holds so many papers. Everything it can see
right now sits on that desk. **If it's not on the desk, Claude can't see it.**
There is no hidden memory — just the desk. (Real name: the *context window*.)

- **New chat = a brand-new empty desk.** Nothing carries over from another day.
- **Long chat = papers pile up and old ones slide off the edge.** That's why it
  "forgets" things from early in a long conversation.

**The fix:** keep the essential papers *pinned* — write them in a file and
reload it every session.

- `AGENTS.md` = the **permanently pinned rules** (always reload at session start).
- `PLAN.md` = the **current task, pinned** so it survives long chats / new days.

A chat message is a *loose* paper (can slide off). A file is a *pinned* paper
(you reload it, so it stays). That's why "put it in the file" beats "just tell
Claude."

> **Good prompting = good desk management.** Put the right papers on, keep the
> important ones from sliding off, don't waste space on junk.

---

## Lever 2 — Tools (MCP)

By default Claude has **no hands** — it can only produce text. It can't send
email or generate a video by itself.

- A **tool** = an ability you wire up and hand to Claude. Once connected, Claude
  can "call" it, and the harness performs the real-world action, then hands the
  result back to the desk.
- **MCP** = a universal plug (like USB) for connecting tools to Claude.
- An **MCP server** = a bundle of tools for one service (fal.ai server = video
  tools; Gmail server = email tools).

**Chef analogy:** the chef can't leave the kitchen, but if you wire a phone to
the grocery store (a tool), the chef can *say* "order onions" and a runner does
it. fal.ai = the grocery store. The MCP server = the phone line.

**Two habits that matter:**
- **Match tools to the job.** Give a project only the tools it needs. Extra
  tools = clutter on the desk + cost/risk (fal.ai spends real money — don't
  leave it plugged into projects that don't need it).
- **Scope accordingly:** everyday tools → connect once, globally. Costly/niche
  tools (fal.ai) → connect only for the projects that use them.

**How you connect a tool:**
- **Claude app (claude.ai / desktop):** Settings → Connectors → click + log in.
- **Claude Code (project/terminal):** add the MCP server's address to config
  (a command like `claude mcp add`, or the project's `.mcp.json`). Newly added
  tools usually load after a **session restart**.

Once loaded, a tool is a **permanent fixture on the desk** — you never
re-announce it. You just ask ("make a video of X") and Claude uses it.

---

## The split that confuses everyone

| | What it is | Where it lives |
|---|---|---|
| `AGENTS.md` | **Rules** (words) | a text file in your project |
| MCP / tools | **Abilities** (connections) | separate config / Connectors — NOT in `AGENTS.md` |

`AGENTS.md` can hold a *rule about* a tool (*"ask before spending fal.ai
credits"*), but the tool's actual connection is wired in elsewhere.

---

## Who does what (the human on the loop)

Let Claude do the mechanical work; you do the human-only parts.

| Task | Whose job |
|---|---|
| Editing the `.mcp.json` config | **Claude** (just ask it) |
| Providing your fal.ai API key / secret | **You** |
| Clicking "connect" / OAuth on a web connector | **You** |
| Approving a costly action before it runs | **You** |

---

## Your running example (the fal.ai video pipeline)

The rule you designed yourself, for `AGENTS.md`:

```
## Rules
- Generating a video on fal.ai costs real money (pay-as-you-go credits).
  Draft the full plan first, then STOP and wait for my approval before
  calling fal.ai. No generation without my go-ahead.
- Never re-generate a video I've already marked wrong. If a request matches
  one I rejected, flag it in the plan and ask before generating.
```

The pattern: **plan cheaply → get approval → execute expensively.** The human
gate sits exactly where the money starts.

---

## Quiz yourself (cover the answers)

1. What's the difference between the model and the harness?
2. Why does Claude "forget" things in a long chat? (Use the desk.)
3. If you want a rule to survive every session, where does it go — a chat
   message or a file? Why?
4. On a fresh Claude with no tools connected, can it generate a fal.ai video?
   Why or why not?
5. What's an MCP server, in one sentence?
6. `AGENTS.md` vs. MCP — which holds rules, which holds abilities?
7. Of these, which can you hand to Claude and which stay yours: editing
   `.mcp.json`, providing your API key, clicking a web connector?

<details>
<summary>Answers</summary>

1. Model = the reasoning engine (skill, no memory/hands). Harness = everything
   you set up around it. Your prompt is part of the harness.
2. The desk is finite; as it fills, old papers slide off — it literally can't
   see them anymore.
3. A file — it's a *pinned* paper you reload each session; a chat message can
   slide off the desk.
4. No — no tool is connected, so it has no hands to reach fal.ai. It can only
   talk about it.
5. A bundle of tools for one service, plugged into Claude via the MCP "port."
6. `AGENTS.md` = rules (words). MCP = abilities (connections).
7. Claude: editing `.mcp.json`. You: API key + clicking the web connector.

</details>

---

*Next up: Lever 3 — Verification (how to stop Claude from breaking things).*
