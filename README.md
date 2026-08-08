# yc-sus-skills-context

Agent skills distilled from all ten public talks at [YC Startup School 2026](https://events.ycombinator.com/startup-school-2026), held July 25 to 26 in San Francisco.

Each talk becomes one skill file an agent can load, plus one long-form notes file for humans. Nothing is merged.

## What is in here

| Speaker | Skill | Notes |
|---|---|---|
| Boris Cherny | `claude-code-method` | `notes/boris-cherny.md` |
| Garry Tan | `personal-agi-method` | `notes/garry-tan.md` |
| Alexandr Wang | `agentic-looping-method` | `notes/alexandr-wang.md` |
| Jensen Huang | `confront-reality-method` | `notes/jensen-huang.md` |
| Sam Altman | `contrarian-conviction-method` | `notes/sam-altman.md` |
| Jeff Dean | `capability-gap-method` | `notes/jeff-dean.md` |
| Patrick Collison | `ambition-sizing-method` | `notes/patrick-collison.md` |
| Dmitri Dolgov | `reliability-nines-method` | `notes/dmitri-dolgov.md` |
| Blake Scholl | `iteration-cost-method` | `notes/blake-scholl.md` |
| Max Hodak | `company-operating-system-method` | `notes/max-hodak.md` |

Two layers. `skills/` holds agent-loadable files with YAML frontmatter, written around trigger conditions. `notes/` holds the longer write-ups those skills were distilled from, each ending with a section on what actually transfers and a section on where the speaker is arguing his own book.

Skills are named for methods rather than speakers on purpose. An agent should load `reliability-nines-method` because it is reasoning about the gap between a demo and a product, not because someone said the word Waymo.

## What each one is for

`claude-code-method` covers deleting accumulated scaffolding on every model release and rebuilding by ablation, why over-specifying prompts now hurts, and verification as the thing that lets an agent run for days instead of minutes.

`personal-agi-method` covers building a context library an agent reads from, the librarian problem of deciding which pages are open at request time, and the split between computation that belongs in the model and computation that belongs in code.

`agentic-looping-method` covers scaling token spend against a single outcome inside a feedback loop, and why the metric has to exist before the swarm does.

`confront-reality-method` covers admitting a technical foundation is wrong and rebuilding on the correct one, from NVIDIA's 1995 near-death.

`contrarian-conviction-method` covers picking work the consensus rejects and holding it for years.

`capability-gap-method` covers a problem-selection gate: hand your problem cold to a frontier model and measure the success rate, because near 0% means a real gap worth building on and 20% means the next scaling step absorbs you.

`ambition-sizing-method` covers choosing how large a first bet to make, tested against whether you want year ten of it.

`reliability-nines-method` covers the exponential ladder between a working demo and a deployable product.

`iteration-cost-method` covers driving down the cost of a single iteration as the thing that sets how fast anything hard gets built.

`company-operating-system-method` covers the internal systems that set a company's speed: purchasing, recruiting, review, budgeting.

## Conventions

One talk, one markdown file. Never combine talks into a shared file.

Each talk gets its own directory under `skills/` containing a single `SKILL.md`. Ten talks means ten directories and ten skill files. Do not merge speakers into a combined overview, do not add an "all talks" summary file, and do not consolidate related talks because their themes overlap. Overlap is expected and is not a reason to combine.

The reason is practical. An agent loads one skill based on its frontmatter description. A merged file either loads for everything or loads for nothing, and it forces the model to read nine irrelevant talks to reach the one that matters.

## Install

For Claude Code, copy the skills you want into your skills directory:

```bash
git clone https://github.com/vinilpolepalli/yc-sus-skills-context
cp -r yc-sus-skills-context/skills/* ~/.claude/skills/
```

Project-scoped instead of global:

```bash
cp -r yc-sus-skills-context/skills/* .claude/skills/
```

Or take one:

```bash
cp -r yc-sus-skills-context/skills/claude-code-method ~/.claude/skills/
```

For any other agent, each `SKILL.md` is plain markdown with YAML frontmatter. Point your harness at it or paste it in.

## The obvious irony

`claude-code-method` says to delete accumulated instruction files, because most of what is in them patches weaknesses of an older model. This repo is ten instruction files.

That is addressed inside the skill rather than papered over. Treat these as starting hypotheses, run them against your own work, and cut whatever does not earn its place. If you install one and never observe it changing an outcome, the Boris skill says to delete it, and it is right.

## Where they disagree with each other

The most useful thing across the set is that the speakers contradict each other, and the contradictions are testable.

Garry Tan and Alexandr Wang argue for accumulating scaffolding, converting every task into a reusable file, and keeping everything. Boris Cherny argues close to the opposite, that you should delete it all on every model release and add back only what you observe the model failing without. He is the one who builds the harness, which makes his dissent hard to wave away.

All three agree the feedback signal is what makes an agent loop work. Tan calls it the librarian and contradiction checks, Wang calls it the metric, Cherny calls it verification. The split is entirely about how much written structure belongs around it.

Similar tension elsewhere in the set. Jeff Dean says to pick problems where the model currently fails almost completely. Boris Cherny says to retry the problems that previously failed on every new model. Those are compatible but they pull in different directions on timing.

## Provenance

Notes are original synthesis and paraphrase written from publicly published transcripts, principally [Root Access](https://www.ycrootaccess.com). No transcript text is reproduced here. Quotes are short and attributed.

Each notes file flags what could not be verified from the source, including figures given on stage without backing, claims that coincide with what the speaker sells, and places where transcripts disagree with each other.

Not affiliated with Y Combinator, Anthropic, or any speaker.

## License

MIT for the notes and skills in this repo. The underlying talks belong to their speakers and to Y Combinator.
