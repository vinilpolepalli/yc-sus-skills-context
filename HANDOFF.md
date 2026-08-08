# Handoff

State of the repo and what is left to build.

## What is here

```
README.md                              repo overview
LICENSE                                MIT
skills/claude-code-method/SKILL.md     the skill
```

## Context on what this is

A skill file distilled from Boris Cherny's YC Startup School 2026 talk on getting
long-horizon autonomous work out of Claude Code. The repo is named for the broader
YC Startup School 2026 set, so it is expected to grow to one skill per speaker.

Ten talks from that event have public recordings. Boris is the only one built so far.
The remaining nine, with YouTube IDs:

| Speaker | Talk | YouTube ID |
|---|---|---|
| Max Hodak | Average Is Not Good Enough | Xc4klGbq8v8 |
| Garry Tan | Own Your Intelligence | eRrc1pUY5oU |
| Dmitri Dolgov | The Demo Is Only 1% Of The Work | Gp4zrV3-6N8 |
| Patrick Collison | Is AI Breaking the Lean Startup Playbook? | 5d6y3poKwK4 |
| Jeff Dean | The 1% Rule for Building in AI | CxXgV54KzpQ |
| Alexandr Wang | This Is a Once-in-a-Civilization Opportunity | sJ4VJWycX9M |
| Blake Scholl | How 50 People Built a Supersonic Jet | byAj35QlGbs |
| Sam Altman | Never a Better Time to Do a Startup | ZIaOBAjvc38 |
| Jensen Huang | The Mindset That Built NVIDIA | I4B37S1dyQQ |

Boris Cherny, We Cut 80% of Claude Code's Prompt, is `qyPCVqFUyDo`.

Four announced speakers had no public recording found as of 2026-08-08:
Tarek Mansour (Kalshi), Chelsea Finn (Physical Intelligence), Max Junestrand (Legora),
Peter Steinberger (OpenClaw).

## Adding more skills

One talk, one markdown file. This is a hard rule, not a default.

Each talk gets its own directory under `skills/` containing a single `SKILL.md` with
YAML frontmatter carrying `name` and `description`. Ten talks means ten directories
and ten files. Do not combine speakers into a shared file, do not add a top-level
"all talks" summary document, and do not merge talks whose themes overlap. Overlap
between them is expected and is not a reason to consolidate.

Write each `description` around trigger conditions, meaning when an agent should load
that skill, rather than as a summary of the talk.

Transcripts for these talks are published at ycrootaccess.com with speaker labels.
Example URL shape: `https://www.ycrootaccess.com/p/jensen-huang-the-mindset-that-built`.
Write original notes from them. Do not commit transcript text to this repo.
