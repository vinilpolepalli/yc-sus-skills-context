---
name: personal-agi-method
description: Method for building a personal context library an agent reads from, deciding whether a computation belongs in the model or in code, and converting finished work into reusable skill files. Use when an agent keeps re-deriving things it already worked out, when deciding what to write down versus retrieve, when an agent fails at arithmetic or state tracking, when setting up recurring jobs, or when someone asks how to get compounding leverage rather than one-off answers. Derived from Garry Tan's YC Startup School 2026 talk.
---

# Personal AGI method

Source: Garry Tan (Y Combinator), YC Startup School 2026, "Own Your Intelligence" / "Personal AGI Is How You Stay Under Your Own Power." Video: https://www.youtube.com/watch?v=eRrc1pUY5oU

## The framing

The claim is that general intelligence is not arriving as a single event. It arrives diffused, as an agent running on your own context, and it looks like infrastructure rather than an announcement.

The distinction Tan draws is between renting and owning. A subscription assistant improves only when the vendor ships. A context library you own improves every day you use it, because every day it holds more of your life. One is a product you consume, the other an asset that compounds.

The practical equation: a frontier model, which is rented and gets cheaper each quarter, plus your own context, which is unique to you, plus a harness wiring them together.

## Library plus librarian

An agent holds on the order of a million tokens, roughly a thousand pages. That sounds large until you compare it to a life, which is not three books but a library.

So the question that decides whether an agent is useful or useless is not how much it can hold. It is who or what decides which pages are open at the moment of the request. That selection step is the librarian, and it is where the engineering actually lives.

Retrieval is the primitive, not the product. Tan's own framing when asked whether this is just RAG: Postgres is just B-trees. The hard parts are what gets written down in the first place, how it gets enriched and linked, what gets promoted to hot memory versus filed as cold reference, and who arbitrates when two stored facts disagree.

## Latent space versus deterministic space

The most portable idea in the talk, and the best debugging heuristic across any of these methods.

Ask where the computation is happening. There are two answers and confusing them causes most agent failures.

Latent space holds taste, judgment, and reading what someone actually wants from a vague request. It lives in the model and you steer it with a markdown file.

Deterministic space holds arithmetic, queries, and state tracking. It belongs in code and a database that the markdown calls.

Tan's example scales the point. Seating five people at a table is fine in latent space. Building schedules for thousands of people requires the agent to write code to track state. The formulation to keep: the model fails where we fail, and the fix is to let it compute the way humans compute, with markdown calling scripts and databases.

When an agent fails, ask which space the failing step was in and whether it belonged there.

## Skill files as employees

A skill file is one capability and one job, written clearly enough that someone new could execute it. Tan's test is that if a competent new hire could follow the page, an agent can run it.

The corollary he draws is that clear written English is now a form of programming, with the model as the compiler. This is why non-engineers on his team build working automations.

## Never do one-off work

The discipline he identifies as separating people who compound from people who dabble.

Most people run one operation, get a result, and close the window, discarding the context. Instead, at the end of a task, convert what was done into a reusable file. His phrasing internally: if you have to ask for something twice, you failed.

It does not matter how capable the model becomes if nothing you learn turns into durable memory.

## Getting started, and the shape of the curve

Start small. His own library began as a folder with a few files about the projects and people he dealt with most, not as an archive. Nobody builds the warehouse first.

Write one page per project and per person covering what you are building together, what they care about, what you owe them, and what was said last time. That information exists only in your head and no model has it.

Then wire one recurring job. The reported curve: week one it feels like a toy, around week four the agent starts answering from your context and the loop catches, and by week twelve it answers before you finish asking. Most people quit in week two.

## The caveat that decides whether this works

Stated in the talk and worth more weight than its length there. A brain nobody curates is a garbage dump with good search.

Retrieval will surface a stale fact with total confidence, and a bad skill file encodes a bad process indefinitely. So the requirement is memory plus hygiene: provenance on stored facts, contradiction checks when new information collides with old, and active pruning. Treated as production infrastructure it compounds. Treated as a dumping ground it produces a confident agent that is wrong in ways nobody can trace.

## Ownership

The argument in the second half of the talk is that a skill file is a piece of cognition made explicit and executable, so the question of who controls that file matters.

The same set of files is either portable expertise that travels with the person who built it, or work extracted from them that keeps running after they leave. The historical parallel offered is that craftsmen owned their tools and that ownership is what made them independent.

Practical instruction: keep your context and skill files in a repository you control from the start.

## Where this disagrees with the room

Tan is the strongest accumulate-scaffolding voice of the event. Alexandr Wang broadly agrees. Boris Cherny argues close to the opposite, that accumulated instruction files mostly patch weaknesses of older models and should be deleted on every model release, with lines added back only after observing repeated failure.

Everyone agrees the feedback signal matters. The split is over how much written structure belongs around it, and it is testable on your own work.
