# Handoff

State of the repo and what is left to build.

## What is here

```
README.md                                            repo overview
LICENSE                                              MIT
skills/claude-code-method/SKILL.md                   Boris Cherny
skills/personal-agi-method/SKILL.md                  Garry Tan
skills/agentic-looping-method/SKILL.md               Alexandr Wang
skills/confront-reality-method/SKILL.md              Jensen Huang
skills/contrarian-conviction-method/SKILL.md         Sam Altman
skills/capability-gap-method/SKILL.md                Jeff Dean
skills/ambition-sizing-method/SKILL.md               Patrick Collison
skills/reliability-nines-method/SKILL.md             Dmitri Dolgov
skills/iteration-cost-method/SKILL.md                Blake Scholl
skills/company-operating-system-method/SKILL.md      Max Hodak
notes/<speaker>.md                                   one long-form notes file per speaker
```

All ten talks with public recordings are covered. Each speaker has both a skill file
and a notes file. The notes are the longer write-up; the skill is the distilled,
agent-loadable version.

## Context on what this is

Skill files distilled from the ten public talks at YC Startup School 2026, held
July 25 to 26 in San Francisco. All ten are built. Each speaker has one skill file
under `skills/` and one long-form notes file under `notes/`.

Transcripts came from ycrootaccess.com, which publishes speaker-labeled transcripts
of these talks. Several are published there under different titles than the YouTube
uploads use, which is worth knowing if you go looking:

| Speaker | YouTube title | Published transcript title | Video ID |
|---|---|---|---|
| Max Hodak | Average Is Not Good Enough | How to Build a Startup That Moves Fast | Xc4klGbq8v8 |
| Dmitri Dolgov | The Demo Is Only 1% Of The Work | Seven Lessons From Building AI for the Physical World | Gp4zrV3-6N8 |
| Patrick Collison | Is AI Breaking the Lean Startup Playbook? | What If You Succeed? | 5d6y3poKwK4 |
| Blake Scholl | How 50 People Built a Supersonic Jet | The Future Was Supposed to Be Faster | byAj35QlGbs |
| Jeff Dean | The 1% Rule for Building in AI | (same) | CxXgV54KzpQ |
| Sam Altman | Never a Better Time to Do a Startup | (same) | ZIaOBAjvc38 |
| Jensen Huang | The Mindset That Built NVIDIA | (same) | I4B37S1dyQQ |
| Boris Cherny | We Cut 80% of Claude Code's Prompt | (same) | qyPCVqFUyDo |
| Alexandr Wang | This Is a Once-in-a-Civilization Opportunity | (same) | sJ4VJWycX9M |
| Garry Tan | Own Your Intelligence | (same) | eRrc1pUY5oU |

Four announced speakers had no public recording found as of 2026-08-08:
Tarek Mansour (Kalshi), Chelsea Finn (Physical Intelligence), Max Junestrand (Legora),
Peter Steinberger (OpenClaw). If recordings appear, they are the next additions.

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
