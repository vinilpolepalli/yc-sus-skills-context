---
name: claude-code-method
description: Operating method for getting long-horizon, autonomous work out of Claude Code and similar agent harnesses. Use when deciding whether to keep or delete a CLAUDE.md, skills, or hooks; when a prompt is being over-specified; when an agent stalls or loops; when setting up verification for a long-running task; when choosing between a workflow, a loop, and a routine; or when someone asks how to get more out of a coding agent. Derived from Boris Cherny's YC Startup School 2026 talk.
---

# Claude Code method

Source: Boris Cherny (Claude Code, Anthropic), YC Startup School 2026, "We Cut 80% of Claude Code's Prompt." Video: https://www.youtube.com/watch?v=qyPCVqFUyDo

These are working notes on how the person who builds the harness says to use it. Apply them as defaults, not as rules to recite back.

## The one-line version

Give the model a task slightly harder than you think it can do, give it a way to check its own work, remove your scaffolding, and let it run.

## 1. Delete before you add

The counterintuitive habit: on every model release, delete your `CLAUDE.md`, your skills, and your hooks.

Rationale. Anthropic deletes roughly 80% of the Claude Code system prompt with each model generation. Most of what accumulates in a prompt is correcting behavior an older model got wrong. Instructions are not free, because the model reads them on every turn, so a stale instruction is active harm rather than neutral baggage. Boris also reports the model tests as slightly more capable with prompts stripped entirely; the prompts exist to make the product behave predictably, not to make the model smarter.

How to rebuild, by ablation rather than guesswork:

1. Delete everything.
2. Use it on real work.
3. Watch where it actually stumbles.
4. Add an instruction back only after the same failure repeats.
5. Add one line at a time and measure the effect of each.

Never predict what the model needs. Observe it.

Two levers mentioned as ablation aids: `CLAUDE_CODE_SIMPLE=1` strips all system prompts including tool prompts, and `--system-prompt` sets your own from scratch. Treat these as undocumented and verify before relying on them.

## 2. Stop over-specifying

The most common failure mode, and it is worst among experienced engineers: writing "do X, then Y, then Z, in this exact way."

That was correct for older models. It is wrong now.

Specify the task at a high level, the guardrails, and the exit criteria. Do not specify the step-by-step procedure, your preferred implementation, or stylistic micromanagement. Then leave and come back.

The mental model is a coworker, not a script interpreter. You would not hand a senior engineer a numbered list of keystrokes.

## 3. Verification is the thing people get wrong

Called out as the single most important thing people fail at.

A long-running agent does not need an elaborate harness. It needs a feedback signal so it can tell whether it is making progress and never gets stuck. Without one it stalls in minutes. With one it runs for days.

Verification signals that work:

- a comprehensive test suite
- screenshots compared pixel by pixel against a reference
- static and dynamic analysis
- fuzzing against known-good behavior
- any oracle that reports correct or not-yet-correct without a human in the loop

Before launching a long task, answer this: how will the agent know it is wrong? If you cannot answer, you do not have a task, you have a wish.

## 4. Give it work that feels too hard

Two examples from the talk.

The Bun runtime, a JavaScript runtime of over 100k lines of low-level systems code, was rewritten from Zig to Rust. One prompt, one dynamic workflow, human steering along the way. It ran for 11 days. The result is in production and is what Claude Code runs on. The reason it worked is that Bun has an exhaustive test suite, which supplied the oracle.

An Electron desktop app was rewritten in Swift from a prompt whose whole content was: rewrite it, run the Electron app in a Mac VM, screenshot it, compare pixel by pixel against the Swift version, and do not stop until done. It ran for over two weeks and started posting screenshots of its own progress to a Slack channel unprompted.

Note what those prompts contain: a hard goal, a verification loop, and a stop condition. Nothing else.

Corollary: keep a set of problems that previously failed and re-attempt them on each new model. The Bun rewrite failed on every model until it suddenly did not. Past failures are not permanent.

## 5. Scale out

Dynamic workflows, for one large task. The invocation is literally "use a workflow." The harness sandboxes a runtime and orchestrates agents as an algebra of sequential stages, parallel fan-out, and verification passes. A common shape is fan out, then a second wave that verifies or summarizes, then fan out again. Use for whole-codebase migrations, deep data analysis, and features spanning many pull requests. This is a distinct axis of test-time compute: not model size, not training FLOPs, not tokens generated, but orchestrated agent-hours at inference time.

Loops and routines, for repetitive tasks. Same task repeatedly, no shared context but shared memory. A loop is a cron job running locally. A routine is the same thing in the cloud so the laptop can close.

Anthropic runs roughly 20 to 30 routines daily across its CLI, iOS, Android, and desktop codebases, each about one sentence long. Worth copying:

- dead code cleanup, finding unreachable code by static and dynamic analysis and opening a daily deletion PR. Nobody specified static analysis; the agent chose it.
- shipping finished experiments, ripping out flags already at 100% rollout
- writing tests for under-covered areas
- deleting low-value tests left by older models
- an "abstraction police" pass that finds near-duplicate abstractions across the codebase and unifies them

The stated direction is fully automated maintenance so humans only do new products and user conversations.

## 6. Evals are the only semi-durable asset

Delete code and prompts freely. Keep appending to evals. But do not get attached: an eval survives roughly one to three model generations before it saturates, at which point throw it out and build a new one from wherever the model now struggles.

Build the eval set from observed failures on your own real work, not from a benchmark.

## 7. Hunt for product overhang

Two sides of one coin. Product overhang is when the model can already do something valuable but no product lets it express that. Hobbling is when your product or scaffolding actively gets in the way.

Claude Code itself was an overhang play. Sonnet 3.5 could write entire files while every coding product of the era offered autocomplete and read-only chat. The move was to remove scaffolding and hand the model a terminal.

Two ways to find more:

1. Throw each new model at a real problem repeatedly over time.
2. Play with no commercial purpose. Someone found that Opus 5 can draw by handing it OpenCV. It was never trained to draw. That is a pure elicitation gap found by messing around.

## 8. Mindset

Be empirical rather than theoretical. This behaves like a natural science: try, observe, adjust. Model behavior resembles a living organism more than a designed system, and each generation has a different personality worth learning.

Drop priors. Big up-front design, exhaustive unit tests, and multi-month re-architectures are now liabilities.

There is no one weird trick. Do not tune your workflow from social media threads.

Escalate in order: repeated stumble means add a targeted instruction or skill; missing context means wire up an MCP. Only after observing the failure.

Known rough edges as of this talk: deep systems code, distributed systems, and pixel-exact UI verification. Vision and computer use improved substantially in Opus 5 without being solved.

## Checklist

- [ ] Delete `CLAUDE.md`, skills, and hooks. Run a week. Add back only what you provably miss.
- [ ] Pick a task you assumed was too hard. Attempt it with a verification loop.
- [ ] On the next big task, write the goal, the guardrails, and the exit criteria, and nothing else.
- [ ] Stand up routines for dead code, test coverage, and duplicate abstractions.
- [ ] Say "use a workflow" on the next multi-stage project.
- [ ] Start an eval set from this week's observed failures. Expect to discard it.
- [ ] Set a reminder to redo all of the above at the next model release.

## A caveat this skill cannot resolve for you

This file is scaffolding, and section 1 tells you to delete scaffolding you have not verified you need. That is not a contradiction so much as an instruction about this document: treat it as a starting hypothesis, run it against your own work, and cut whatever does not earn its place.

There is also a live disagreement worth knowing. At the same event, Alexandr Wang and Garry Tan both argued for accumulating scaffolding rather than deleting it, Tan most strongly, with a personal knowledge base of roughly 220,000 markdown files and a rule to convert every task into a reusable skill file. OpenAI's published guidance on long-horizon Codex tasks also recommends building structure: a spec file, a plans file with checkpointed milestones, a runbook, and a status log.

All parties agree the feedback signal is what makes an agent loop work. They disagree about how much written structure should surround it. That disagreement is empirical and testable on your own repository, which is a better use of an afternoon than picking a side from a talk.
