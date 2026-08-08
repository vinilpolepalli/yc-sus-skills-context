---
name: capability-gap-method
description: Method for choosing problems by measuring where frontier models fail completely, sizing bottlenecks with first-principles arithmetic, and closing the gap with context and specialized systems rather than retraining. Use when deciding what to build or which problem to attack next, when judging whether a capability will be absorbed by the next model release, when an agent goes off the rails partway through a long task, when a performance or cost question needs an order-of-magnitude answer before any code is written, or when someone asks where a small team can still beat a large lab. Derived from Jeff Dean's YC Startup School 2026 talk.
---

# Capability gap method

Source: Jeff Dean (Google), YC Startup School 2026, "The 1% Rule for Building in AI," interviewed by Diana Hu. Video: https://www.youtube.com/watch?v=CxXgV54KzpQ

The method has three parts that run in order: pick the problem by measuring model failure, size it with arithmetic before building, then close it with context and tools instead of weights.

## 1. Score the problem before committing to it

Before building anything on top of a model, hand the raw problem to a frontier model with no scaffolding and measure how often it succeeds.

Read the score this way:

- Near 0% or 1%: a real capability gap. Whatever you build to close it is doing work the general model is not about to do incidentally.
- Around 20%: the model half does it already. The next scaling step finishes it and your work becomes a patch on a capability that arrives for free.

Dean's phrasing: "Look for something where the model succeeds 0% or 1% of the time, not 20%."

This is a gate, not a vibe. Run it as an actual eval with real inputs from the domain, not a handful of prompts you liked. Log the score so you can rerun it on the next model release.

Then ask the durability question, which is where the method stops giving you answers: does this gap hold for six to twelve months or for two to three years? Nothing in the method decides this. If you cannot argue it, you are gambling, and you should at least know that you are.

## 2. Do the arithmetic before the engineering

The habit that produced the TPU was one multiplication done years before the problem arrived. In 2013 deep nets halved speech recognition error rates and cost far more to serve. The calculation: if every user talked to their phone for three minutes a day, Google would have to double its entire server fleet. That number, not a research agenda, justified custom silicon.

Apply it as a procedure:

1. Name the dominant cost or bottleneck in your system.
2. Project it under success rather than current usage. Assume the thing works and people use it.
3. If the answer is absurd, you have found the real problem.
4. Ask from first principles whether a structurally different approach gives one to two orders of magnitude, rather than tuning what everyone currently does.

Corollary from the TPU design: when you specialize, specialize one level more general than the problem in front of you. They built a low-precision linear algebra engine, not a speech-model chip. The Transformer was invented years later and the hardware survived it. A chip tuned to 2013's architectures would have been scrap.

## 3. Reason in energy and movement, not time

The number that governs modern systems: a multiply costs roughly one picojoule, and moving the operand in from HBM costs about a thousand times that. Compute is nearly free. Movement is the bill.

What to keep in your head when reasoning about an ML system:

- memory bandwidth from main memory to on-chip memory to the multiplier units
- energy per multiply
- interconnect bandwidth between chips
- how badly scaling falls off talking to 10,000 chips instead of 500

Most things that present as model problems are movement problems. Batching exists to amortize the 1000x penalty, which is why batch-size-one training is impractical and why batching fights low-latency inference. When a system is slow or expensive, ask what is moving and how far before you ask what is computing.

## 4. Fix failures with context, not weights

Training data gets compressed into parameters and becomes opaque. Context is text the model reads and reasons about directly, so it is legible and iterable in a way weights are not.

The loop:

1. Run the model on the real domain problem.
2. Watch where it fails.
3. Fix the failure by writing a better skill, a clearer tool definition, or a usage guideline.
4. Rerun. Do not reach for fine-tuning until this stops paying.

The specific move worth copying: take expertise that currently lives only in someone's head and write it down as a document the agent reads. Dean and Sanjay Ghemawat published a roughly 30-page "Performance Hints" document that encodes low-level optimization knowledge. It now steers models. Whatever your team knows and has never written down is the same asset.

Their self-improving loop, mechanically: the agent writes microbenchmarks for a library, edits the library code, reruns the benchmarks, measures cache footprint, and iterates unattended. Dean's own verdict is measured, that it worked well for some kinds of problems. Do not expect this to transfer to work without a fast scoring function.

## 5. Keep long-running agents on the lit path

Agents are reliable to roughly step 10. Most people have watched one go off the rails around step 30 or 40. The cause is drift off-distribution: each step lands somewhere slightly less like anything in training, and errors compound.

Four mitigations, in the order they are cheap:

- Give the model skills and hints that keep it on territory where it is already competent.
- Give it tools to query its environment: run the review, take the measurement, fetch the logs. An agent reasoning in the dark drifts faster.
- Run several agents on different approaches, with a separate evaluator picking promising branches. This spends inference compute on breadth rather than depth.
- Search over candidate solutions and keep what scores well.

Write the spec more carefully than you would for a human. A person asks a clarifying question, an agent does not. Dean: "The importance of specifying what you want has actually gone up." The task type that works unusually well is translating an existing implementation into another language, precisely because the source is itself an exact spec.

## 6. Automate the loop only where the evaluator is fast

Propose a candidate, implement it, evaluate it, keep what works, integrate. This is what AlphaChip does for layout and AlphaEvolve does for solutions, and it generalizes to anything with a measurable objective.

The evaluator is the whole constraint. In quantum chemistry, a neural approximation of a density functional theory simulator runs about 300,000 times faster and is nearly as accurate, which turns a compute campaign into something interactive and changes which questions get asked at all.

So before setting up any self-improving loop, answer one question: can you score a candidate cheaply and trustworthily? If not, the loop does not close, and more agents make it worse rather than better. Building the evaluator first is the work.

## 7. Where a small team still has room

Large labs optimize for general capability across every domain at once, which structurally means no single niche gets specialized attention. The openings:

- A user's own data. The general model organizes public information and does not hold your user's context.
- Narrow models trained on domain data, affordable at niche scale and uneconomic for a general lab. AlphaFold is the shape of the argument.
- A purpose-built surface for a domain, where the interaction and the tooling beat a generic chat box.

Each of these still consumes a general model rather than replacing one. That is a real strategy and also the strategy that most benefits the incumbent describing it.

## 8. Calibrate judgment on a twelve-month clock

Once agents write most of the code, the scarce input is deciding what to work on.

The one mechanical practice offered: write down what you think will matter over the next twelve months, then come back in twelve months and grade which items actually did. Repeat. This is the only feedback signal most people will ever get on their strategic calls, and it costs about an hour a month.

The complementary practice: attack an assumption the field treats as fixed. Chips assume transistors are essentially perfectly reliable. What would you build if a transistor made twenty errors a day instead of one per million years? The 0% rule and the TPU are both instances of refusing to inherit a constraint.

Selection criterion for any project: if this works out as well as it possibly could, is the world meaningfully better? If not, do not spend the time.

## Checklist

- [ ] Score your core problem cold against a frontier model. Write the number down.
- [ ] If it scored around 20%, decide what you are building instead.
- [ ] Argue the durability window out loud, and note that this step has no method.
- [ ] Project your dominant cost forward assuming success. Check whether the answer is absurd.
- [ ] Ask what is moving before asking what is computing.
- [ ] Write down one piece of expertise your team has never documented, and point an agent at it.
- [ ] Before any self-improving loop, build the evaluator and confirm it is fast.
- [ ] Start the prediction journal. Set a reminder for twelve months out.

## What this method does not cover

It selects problems and sizes them. It says nothing about distribution, pricing, or whether anyone wants the thing. The durability question is left open, which is exactly the judgment that decides whether a 0% problem becomes a company or a two-year detour.
