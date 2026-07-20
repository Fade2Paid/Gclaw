# AGENTS.md — YouTube Video Pipeline

> Operating rules for the automated pipeline: pick a niche → write a script →
> generate the video on Higgsfield → publish to YouTube. Keep this file short
> and high-signal. Fill in every <blank>.

---

## 1. What this project is

- **Product:** a short-video pipeline. Given a niche, it produces a script,
  generates the video on Higgsfield, and hands you a finished video ready to
  post. **You do the actual YouTube posting yourself.**
- **Niche:** <your chosen niche — e.g., "60-second personal-finance tips">
- **Runtime:** Claude orchestrating MCP tools (Higgsfield for generation,
  YouTube for publishing).
- **Video format target:** <e.g., 9:16 vertical, 30–60 sec, for YouTube Shorts>

## 2. How to work here (the loop, in pipeline order)

1. **Draft the script** for the chosen niche.
2. **STOP — get my approval on the script** before generating anything.
3. **Generate the video** on Higgsfield (this spends credits).
4. **Run the auto-checks** (section 4) on the result.
5. **STOP — show me the video for approval** (does it look right / on-brand).
6. **Deliver the approved video to me**, plus a suggested title + description.
7. **I post it to YouTube myself** — Claude does NOT post. Then log what was made.

## 3. Tools

- **Higgsfield** MCP server → script assist + image/video generation.
- **YouTube posting is manual (done by me)** — no YouTube tool needed for now.
- Connect Higgsfield **once**, scoped to this project. Don't add unrelated tools.

## 4. Verification

**Objective checks — Claude runs these on every video before showing me:**
- Duration is within the target range.
- Aspect ratio matches the format target.
- It is **not** a duplicate of a video I already rejected (check the reject log).

**Subjective check — that's ME:**
- Does it look good and match the niche/style? I approve or reject.

> A video is **done** only when the objective checks pass **AND** I approve it.

## 5. Tool & permission boundaries (the money gate + the public gate)

- **Money gate:** generating on Higgsfield costs real credits. **NEVER generate
  without my approval of the script/plan first.**
- **Public gate:** Claude **never** posts to YouTube. It prepares the final video
  + title/description and hands off; **I publish manually.** (The riskiest,
  public step stays fully in my hands.)
- **No repeats:** never re-generate a video I've marked wrong. If a request
  looks like one I rejected, flag it and ask before generating.
- **Ask first before:** changing the niche, changing YouTube settings (title,
  description, visibility, schedule), spending credits, or adding new tools.
- **Never:** post to YouTube (that's my job), hard-code API keys, or mark a
  video "done" without my approval.

## 6. Definition of done (per video)

- [ ] Script approved by me.
- [ ] Video generated; objective checks pass (duration, ratio, not a duplicate).
- [ ] I approved the final video (the taste test).
- [ ] Delivered to me ready to post: the final video + a suggested title and
      description. (I do the posting.)
- [ ] Logged: niche, script, video file/id.

## 7. Reject log

Keep a running list of rejected videos (and why) so step 4's duplicate check
works. One line each: `<date> — <short description> — rejected because <reason>`.

---
> Every rule here exists to prevent a specific, costly mistake (wasted credits,
> a bad public post, a repeated reject). When you fully trust a step, you can
> loosen its gate — smallest harness that still works.
