# Getting the Most Out of Claude Code
### Distilled from Boris Cherny's YC Startup School talk

---

## The one-sentence version

Give Claude a task slightly harder than you think it can handle, give it a way to
*verify its own work*, strip away your scaffolding, and let it run.

---

## 1. Delete before you add

The single most counterintuitive habit: **every new model release, press delete.**

- Delete your `CLAUDE.md`. Delete your skills. Delete your hooks. Delete your custom
  system prompts.
- Anthropic deletes ~80% of the Claude Code system prompt with each model generation.
  Most of what's in a prompt is correcting behaviors the *old* model got wrong.
- Instructions are not free, because the model reads them on every single turn. A stale
  instruction is active harm, not neutral baggage.

**How to rebuild:** ablation, not guesswork.

1. Delete everything.
2. Use it normally on real work.
3. Watch where it actually stumbles.
4. Only when you see it fail **repeatedly on the same thing** do you add an instruction back.
5. Add back one line at a time and measure the impact of each.

Never predict what the model needs. Observe it.

**Two undocumented levers mentioned in the talk** (useful as ablation tools):

- `CLAUDE_CODE_SIMPLE=1 claude` strips all system prompts, including tool prompts.
- `--system-prompt` sets your own from scratch.

Notably, the model is often *slightly more intelligent* with the prompts stripped. The
prompts exist to make the **product** behave well, not to make the model smarter.

---

## 2. Stop over-specifying

The most common failure mode, especially among experienced engineers: writing
"do X, then Y, then Z, in this exact way."

That was the right approach for older models. It is the wrong approach now.

**Instead, specify three things:**

| Give it | Don't give it |
|---|---|
| The task, at a high level | Step-by-step procedure |
| The guardrails / constraints | Your preferred implementation |
| The exit criteria ("done when…") | Micromanagement of style |

Then walk away and come back later.

The mental model is a **coworker**, not a script interpreter. You wouldn't hand a senior
engineer a numbered list of keystrokes.

---

## 3. Verification is the thing everyone gets wrong

This is called out as *the single most important thing people fail at*.

A long-running agent doesn't need a fancy harness. It needs a **feedback signal** so it
can tell whether it's making progress and never gets stuck. Without one, it stalls in
minutes. With one, it runs for days.

Good verification signals:

- A comprehensive **test suite** (this is what made the Bun rewrite possible)
- **Screenshots + pixel-by-pixel comparison** against a reference (the Swift rewrite)
- **Static and dynamic analysis**
- **Fuzzing** against known-good behavior
- Any oracle that says "correct / not yet correct" without you in the loop

Rule of thumb: before you launch a long task, ask *"how will Claude know it's wrong?"*
If you can't answer that, you don't have a task, you have a wish.

---

## 4. Give it tasks that feel too hard

Two real examples from the talk:

**The Bun rewrite.** The Bun JavaScript runtime, over 100k lines of low-level systems
code, was rewritten from Zig to Rust. One prompt, one dynamic workflow, steering
along the way. **It ran for 11 days.** It's in production now; it's what Claude Code
runs on. A human team would have needed well over a year.

**The Swift rewrite.** The prompt, roughly verbatim:

> "Rewrite the Electron app in Swift. Run the Electron app in the Mac VM, screenshot it,
> compare it pixel by pixel to the Swift version, and don't stop until you're done."

That's it. It ran for **over two weeks** and spontaneously started live-blogging its own
progress to a Slack channel with screenshots.

Note what's in that prompt: a hard goal, a verification loop, and a stop condition.
Nothing else.

**Corollary:** keep a set of "impossible" problems around and throw each new model
release at them. The Bun rewrite failed on every model until it suddenly didn't. Your
past failures are not permanent.

---

## 5. Scale out: workflows, loops, and routines

### Dynamic workflows, for one big task

Just say **"use a workflow."** That's the whole invocation.

Claude spins up a sandboxed runtime and orchestrates agents as a proper algebra:
sequential stages, parallel fan-out, verification passes. A typical shape:

```
fan out (first pass) → second wave verifies/summarizes → fan out again
```

This is a genuinely new axis of test-time compute. Historically scaling meant model
size, data, and training FLOPs; then it meant tokens generated. Dynamic workflows
scale *orchestrated* agent-hours at inference time.

Use it for: whole-codebase migrations, deep data analysis, features spanning dozens of PRs.

### Loops and routines, for repetitive tasks

Same task, over and over, no shared context (but shared memory).

- **Loop** = cron job running locally
- **Routine** = the same thing running in the cloud, so you can close your laptop

Anthropic runs roughly 20 to 30 of these daily across the CLI, iOS, Android, and desktop
codebases. Each is roughly **one sentence**. Real examples worth stealing:

- **Dead code cleanup.** Finds unreachable code via static + dynamic analysis, opens a
  daily PR to delete it. (Nobody told it to use static analysis; it figured that out.)
- **Ship finished experiments.** Experiment is at 100%? Rip out the flag and ship it.
- **Test coverage.** Write tests for under-covered areas.
- **Test deletion.** Remove low-value tests left behind by older models.
- **Abstraction police.** Scan for near-duplicate abstractions across the codebase and
  unify them.

The goal they're moving toward: **fully automated maintenance**, so humans only do the
fun part, new products and talking to users.

---

## 6. Evals are your only semi-durable asset

- Code and prompts: **delete freely.**
- Evals: **keep appending.**
- But don't get attached. An eval survives maybe one to three model generations before
  it saturates, and then you throw it away and build a new one from wherever the model
  now struggles.

Your eval set should always be built from *observed* failures on *your* real work.

---

## 7. Hunt for product overhang

Two sides of the same coin:

- **Product overhang.** The model can already do something valuable, but no product
  lets it express that.
- **Hobbling.** Your product or scaffolding is actively getting in the way.

Claude Code itself was an overhang play: Sonnet 3.5 could write entire files, but every
coding product at the time only offered autocomplete and read-only chat. The move was
to *remove* scaffolding and hand the model a terminal.

The claim: there are probably **hundreds** of comparable opportunities sitting in
today's models, unclaimed.

**How to find them:**

1. Take a real problem and throw each new model at it, repeatedly, over time.
2. Play. Do creative things with no commercial purpose. (Someone at Anthropic discovered
   Opus 5 can *draw*, doing portraits, animals, and landscapes, by handing it OpenCV. It was
   never trained to draw. Pure elicitation gap, found by messing around.)

---

## 8. Mindset

- **Be empirical, not theoretical.** This is now a natural science. Try, observe, adjust.
  Model behavior is closer to a living organism than a designed system, and each generation
  has a different personality you have to get to know.
- **Drop your priors.** Big up-front design, exhaustive unit tests, months-long
  re-architectures. That instinct is now a liability.
- **Ignore the "one weird trick" crowd.** There is no secret prompt. Don't optimize your
  workflow off LinkedIn and Twitter threads.
- **Own your escalation path.** Repeated stumble → add a targeted instruction or skill.
  Missing context → wire up an MCP. In that order, and only after observing the failure.
- **Know the remaining rough edges.** Deep systems code, distributed systems, and
  pixel-exact UI verification are still imperfect. Opus 5 made a big jump in vision and
  computer use, but it's not solved.

---

## 9. For anyone still learning to build

Learn computer science *by applying it*. The advice is to always be solving an actual
problem you have. That's how Boris learned, writing BASIC on a TI-83 to beat his math
tests, then dropping to assembly when calculus outgrew BASIC.

The durable skills to develop by hand: design sense, business sense, data science,
talking to users. CS plus those is where the value is.

Start by making something *you* want. Then make something people want.

---

## Starter checklist

- [ ] Delete `CLAUDE.md`, skills, and hooks. Run for a week. Add back only what you
      provably miss.
- [ ] Pick one task you assumed was too hard. Attempt it with a verification loop.
- [ ] For your next big task: write the goal, the guardrails, the exit criteria, and
      nothing else.
- [ ] Set up three routines: dead code, test coverage, duplicate abstractions.
- [ ] Say "use a workflow" on your next multi-stage project.
- [ ] Start an eval set from the failures you observe this week. Expect to throw it away.
- [ ] Schedule a recurring reminder to redo all of the above at the next model release.
