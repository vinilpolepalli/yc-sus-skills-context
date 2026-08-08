# yc-sus-skills-context

Agent skills distilled from YC Startup School 2026 talks. One talk, one skill file.

First up is Boris Cherny's [We Cut 80% of Claude Code's Prompt](https://www.youtube.com/watch?v=qyPCVqFUyDo). Boris created Claude Code. The talk is the person who builds the harness explaining how to use it, which makes it worth more than the usual advice layer. This repo packages that method as a skill file an agent can load.

## What is in here

```
skills/claude-code-method/SKILL.md
```

One skill so far. `HANDOFF.md` tracks the remaining talks with recordings, so the next skill starts from a list rather than from scratch. The Boris skill covers deleting scaffolding on every model release and rebuilding by ablation, why over-specifying prompts now hurts, verification as the thing that makes long-running agents work at all, when to reach for a dynamic workflow versus a loop versus a routine, treating evals as the only semi-durable asset, and hunting for product overhang.

## Conventions

One talk, one markdown file. Never combine talks into a shared file.

Each talk gets its own directory under `skills/` containing a single `SKILL.md`. Ten talks means ten directories and ten skill files. Do not merge speakers into a combined overview, do not add an "all talks" summary file, and do not consolidate related talks because their themes overlap. Overlap is expected and is not a reason to combine.

The reason is practical. An agent loads one skill based on its frontmatter description. A merged file either loads for everything or loads for nothing, and it forces the model to read nine irrelevant talks to reach the one that matters.

## Install

For Claude Code, copy the skill into your skills directory:

```bash
git clone https://github.com/vinilpolepalli/yc-sus-skills-context
cp -r yc-sus-skills-context/skills/claude-code-method ~/.claude/skills/
```

Project-scoped instead of global:

```bash
cp -r yc-sus-skills-context/skills/claude-code-method .claude/skills/
```

For any other agent, `SKILL.md` is plain markdown with YAML frontmatter. Point your harness at it or paste it in.

## When it triggers

The skill is written to load when someone is deciding whether to keep a `CLAUDE.md`, when a prompt is being over-specified, when an agent stalls or loops, when setting up verification for a long-running task, or when choosing between a workflow, a loop, and a routine.

## The obvious irony

The talk's central advice is to delete accumulated instruction files because most of what is in them patches weaknesses of an older model. This repo is an instruction file.

That is addressed in the skill's final section rather than papered over. Treat it as a starting hypothesis, run it against your own work, and cut whatever does not earn its place. If you install this and never observe it changing an outcome, section 1 says to delete it, and section 1 is right.

## Where it disagrees with the room

At the same event, Alexandr Wang and Garry Tan both argued the opposite: accumulate scaffolding, convert every task into a reusable skill file, keep everything. OpenAI's guidance on long-horizon Codex work recommends the same, down to a spec file and a status log.

Everyone agrees the feedback signal is what makes an agent loop work. The disagreement is entirely about how much written structure should surround it, and it is testable on your own repository.

## Provenance

Notes are original synthesis and paraphrase from the public recording, not a transcript. Quotes are short and attributed. Not affiliated with Y Combinator or Anthropic.

## License

MIT for the notes in this repo. The underlying talk belongs to its speaker and to Y Combinator.
