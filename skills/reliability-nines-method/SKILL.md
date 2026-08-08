---
name: reliability-nines-method
description: Method for reasoning about the gap between a working demo and a deployable product, using reliability nines, closed-loop evaluation, and simulator-generated edge cases. Use when a prototype works but shipping keeps slipping; when deciding between a human-in-the-loop product and a fully autonomous one; when someone claims a system is "basically done" after one impressive run; when choosing a technology whose current slope looks good but whose ceiling is unknown; when setting up evals for an agent whose actions change its own next input; or when a fast iteration loop is producing no measurable progress. Derived from Dmitri Dolgov's YC Startup School 2026 talk.
---

# Reliability nines method

Source: Dmitri Dolgov (Co-CEO, Waymo), YC Startup School 2026, "The Demo Is Only 1% Of The Work." Video: https://www.youtube.com/watch?v=Gp4zrV3-6N8

Waymo reached a demo-quality autonomous driver in about eighteen months with a
dozen engineers. The product took fifteen years. This file is about the thirteen
years in between, and how to reason about that gap before you enter it.

## The core claim

Reliability is exponential, not linear. Each additional nine of reliability costs
roughly ten times the effort of the previous one. The methods that earn the early
nines do not earn the later ones.

- 90%, one nine: enough for a demo. Ordinary engineering gets you here.
- 99% to 99.9%: enough for a copilot or assist product, where a human catches
  failures and absorbs the cost.
- Beyond that: required for anything that removes the human. Reached only through
  redundancy, tiered fallbacks, and architectural change, never through more of
  the same effort.

Practical consequence: doing the current thing for longer does not move you up the
ladder. When progress stalls at a plateau, the question is not "how do we push
harder" but "what different architecture does the next nine require."

## Before building, answer these

1. What reliability does the product actually need? Write the number.
2. Who absorbs failures? If the answer is a human in the loop, you need far fewer
   nines than you think. If the answer is nobody, you need far more.
3. At your target volume, how often does a once-in-a-million event occur? At scale,
   rare events become daily events. Rarity is a property of your traffic, not of
   the event.
4. What is the ceiling of the approach you picked, not its current slope?
5. How will you know you are wrong, without a human looking?

If question 5 has no answer, stop and build the eval first.

## Count nines, not demo views

Diagnostic questions for any impressive result. Was that one run or the
distribution? Ask for the failure rate over N attempts, not the best attempt. What
was excluded? Demos run inside a chosen envelope, so name the envelope. Does the
demo's cost profile match the product's? Money spent making a demo spectacular is
money not spent on the nines, and they feel like the same budget.

Treat a compelling single run as evidence of one nine and nothing more.

## Build the eval before the technology

Stated as an ordering rule, not a nicety: the eval comes before the system, and the
metrics come before the product.

Three requirements.

**Closed loop, not open loop.** Open-loop evaluation scores passive input-output
pairs against a fixed dataset. Closed-loop lets the action change the world, update
the inputs, and drive the next action. Any agent whose output becomes part of its
next input has this structure, and open-loop scores flatter it by hiding
compounding error.

**System level, not model level.** Evaluate every layer that ships, including
surrounding software, fallback paths, and operational processes. The thing deployed
is not the model.

**Built from your own observed failures**, not a public benchmark.

The strategic argument: models leak and algorithms get replicated, but a large
corpus of evaluated real-world operation is hard to copy. A durable advantage is
more likely in the eval set and the operating record than in the model.

## Simulate the tail you cannot wait for

The long tail arrives too slowly to wait for at the rate a product needs it.
Generating it is a first-class engineering project, not tooling.

Treat the simulator as a significant model in its own right and resource it that
way. It needs behavioral realism (how the world and its actors behave) and, if your
system consumes raw inputs end to end, input-level realism too. A simulator that
emits clean abstractions cannot evaluate a system that eats raw data. Deliberately
generate scenarios you have never observed, including implausible ones. Ground it
in real deployment data continuously, or it drifts into testing a world you do not
operate in.

## Adopting a new technology wave

For each new model, framework, or paradigm, ask three questions, not one:

1. What performance does it give me?
2. Has it simplified my stack?
3. Does it unify or fragment?

Performance alone is insufficient grounds to adopt. The named failure mode is a
successful skunkworks effort that produces a better result with no integration
path, leaving the team carrying two systems permanently. For a small team that is
often fatal.

The hard part is never the research. It is carrying new work into production
without regressions while the existing product keeps running.

## Structure that channels scale

General methods that leverage compute and data beat handcrafted knowledge. That
does not mean all structure is bad. The distinction:

- Structure that fights scale loses. Hand-coded rules that override or constrain
  what the model would learn.
- Structure that channels scale wins. Representations, interfaces, and
  intermediate state that give the model a better substrate to learn on.

Applied form: alongside the learned representation, materialize an explicit
intermediate state you can inspect. That buys a validation layer at inference which
checks something legible instead of trusting the output blindly, cheaper evaluation
against the compact representation, and verifiable feedback signals usable for
reinforcement learning and loss design.

## Point the flywheel

The loop is: deploy, collect data, ground the simulator, generate harder cases,
improve the system, redeploy.

The loop is not the lesson. The caveat is. A flywheel spins in any direction, or in
place. Metrics are the only thing that give it a direction. If you cannot name the
number your iteration loop is supposed to move, you are iterating in place and the
speed of the loop is irrelevant.

## Do not anchor on today's prices

Component costs, token prices, and model capability all move fast enough to
invalidate a plan built on current values. Betting the company on a number with a
short shelf life is a specific and common error. Plan against the trend line and
state the assumption explicitly so it can be rechecked.

## Checklist

- [ ] Write the reliability target as a number before building, and name who
      absorbs failures.
- [ ] Build the eval set first, from your own failures.
- [ ] Convert any open-loop eval to closed-loop where actions affect later inputs.
- [ ] Extend evaluation past the model to the full deployed system.
- [ ] Compute how often your rare failure occurs at target volume.
- [ ] Ask the ceiling question about your core technical bet, in writing.
- [ ] For the next framework adoption, answer simplify and unify, not just faster.
- [ ] Name the single metric your iteration loop moves.

## Limits of this method

This comes from a company with an unusual amount of time and capital, and the
fifteen-year timeline is not a template most teams can copy. The transferable parts
are the nines arithmetic, the eval ordering, and the closed-loop requirement, all of
which are cheap. The parts that require a large simulator team and a fleet are not.

The talk also argues for a specific expensive sensing stack as a general principle
about technology curves. That argument is a prediction about where a competing
curve flattens, made by the party with the most invested in the answer. The ceiling
question is worth asking. The specific answer given is not settled.
