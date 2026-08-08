---
name: confront-reality-method
description: Method for surviving the discovery that a project's technical foundation is wrong, learning an unfamiliar domain fast enough to replace it, and reasoning about systems rather than implementations. Use when evidence suggests a core architectural assumption is invalid and the team is arguing about whether to admit it; when a plan requires expertise nobody on the team has; when deciding what to tell a customer or stakeholder about a failure you caused; when choosing which constraint in a system to optimize; when evaluating whether a new capability is general or narrow; or when work has stalled because the remaining difficulty looks overwhelming. Derived from Jensen Huang's YC Startup School 2026 talk.
---

# Confront reality method

Source: Jensen Huang (NVIDIA), interviewed by Garry Tan, YC Startup School 2026, "The Mindset That Built NVIDIA." Video: https://www.youtube.com/watch?v=I4B37S1dyQQ

The talk is a founder story. What is extractable is a small set of moves for the situation
where the thing you built on turns out to be wrong. Apply these as defaults.

## The one-line version

Treat the technology as replaceable and the project as the thing to preserve, admit the
foundation is wrong the moment you can prove it, acquire the missing skill directly, and
shorten your time horizon until the work is possible again.

## 1. Name the founding assumption, then price its failure

Every project rests on one or two technical assumptions chosen early and never re-examined.
NVIDIA's was the rendering algorithm it was founded on in 1993. It was wrong, and nobody
noticed until 1995.

At the start of any nontrivial task, write down the assumption as a falsifiable sentence, the
observation that would disconfirm it, and what the plan becomes if it is disconfirmed. If you
cannot state the disconfirming observation, you will not notice it arriving.

## 2. When the evidence lands, say so in the same turn

The failure mode is not missing the evidence. It is knowing and continuing.

Jensen's framing was that the company would not exist if it did not confront the fact that the
approach did not work and start on the right one. The admission was the act that saved it,
not the rewrite that followed.

When you discover mid-task that an approach cannot work, say it in the same response where
you discovered it, and say what is wrong at the level of the assumption rather than the
symptom. Do not keep patching around it because a rewrite is expensive or because you
proposed the original approach. Do not bury it at the end of a long tool sequence. Sunk work
is not evidence, and rewrite cost is not an argument about correctness.

## 3. Buy the textbook

The recovery was three OpenGL textbooks from Fry's, handed to engineers who did not know the
correct approach.

When a task needs expertise you lack, read the actual source material and reason from it:
the specification, the RFC, the paper, the library source. Do not route around the gap with a
workaround, guess from adjacent knowledge, build on a summary when the primary source is
reachable, or declare the task blocked. Lacking a skill is a temporary state with a known
remedy.

## 4. Two questions for any new capability

Jensen's stated reasoning loop, applied to chain of thought and to deep learning:

1. If this, then what? Propagate the change forward through the system. What breaks, what
   becomes cheap, what becomes unnecessary.
2. If this gets better, so what? Assume it improves on trend. Does anything you care about
   change.

The second is the filter. Most things pass the first and fail the second. Ask both before
committing effort to something new.

Related test: general or domain-specific? His claim about deep learning is that the important
property was not image recognition but being a universal function approximator. When
something is general, ask which layers of your stack it invalidates, not which feature it
improves.

## 5. Ask which resource is binding

His definition of systems thinking is a list of questions, and they are the useful part:

- What is the problem and what are the constraints?
- Where is the input, where is the output?
- Where does information come from, and at what rate does it flow in and out?
- Is the limit the processor, the memory, or the network?

That last question is the habit. Do not ask whether a system is fast. Ask which resource is
binding, then optimize only that. Outside computing the same question applies to people,
cash, and distribution. His argument for why this matters now is that low-level
implementation is being automated, so the scarce skill is holding the whole system in your
head. He sells full-stack systems, so weight the claim accordingly.

## 6. Report failure upward before it is discovered

NVIDIA had a $12 million contract with Sega for the Dreamcast, built on the architecture just
proven wrong. Jensen flew to Japan, told Sega's CEO it would not work, then asked to be paid
anyway because the company would die otherwise. He got roughly $5 million, which funded the
rewrite.

The copyable part is the disclosure, in person, before discovery. The ask is not generally
copyable: it worked because the relationship and the reasoning both carried it, and you
usually cannot know that in advance. The transferable rule is that when you cause a failure
affecting someone downstream, you want to be the one who reports it. Every option you keep
comes from that.

## 7. Build for control, not for accuracy

On agents, his claim is that people optimize the wrong variable. Accuracy of 80% is fine.
What is missing is the ability to reach into an output and change one specific piece, one
pixel, one triangle, one component, instead of accepting or rerunning the whole thing.

Applied to anything you build or produce:

- Emit output in units a human can edit individually.
- Make the reasoning visible so a reviewer can correct the step rather than the conclusion.
- Prefer a partial result with clear seams over a monolithic result that is slightly better.

An 80% output that composes with a human beats a 95% output that is all-or-nothing.

## 8. Shrink the horizon when the work looks impossible

Two devices, both deliberate rather than accurate. "How hard can it be?" He is explicit that
this underestimates and that things always turn out much harder. It is chosen because the
accurate estimate produces paralysis. What makes it defensible is the paired belief that you
can learn whatever the task requires, the same claim the textbooks make. The other: you do
not overcome the whole thing at once, you overcome the morning.

Stalled on scope? Stop estimating the full task. Do the next verifiable step, then
re-estimate. Estimation is what stalled you.

## Checklist

- [ ] State the founding assumption and its disconfirming observation before starting.
- [ ] On discovering the approach is wrong, say so in that same response.
- [ ] Read the primary source rather than working around a knowledge gap.
- [ ] Ask both questions of anything new: if this then what, if this improves then so what.
- [ ] Name the binding constraint before optimizing anything.
- [ ] Report a failure you caused before the affected party finds it.
- [ ] Make output editable in pieces before making it more accurate.
- [ ] When stalled on scope, do the next verifiable step instead of estimating the rest.

## What this method does not give you

The story is told from the far end of a long survivorship funnel. Jensen mentions 35 to 40
competitors building PC 3D graphics in 1995 and never says how many died doing roughly what
he did. Honest disclosure plus a hard rewrite is a plan that also produces failures.

"How hard can it be" is easier to hold with a strong balance sheet than with eight months of
runway. The stance is useful; it is not a substitute for knowing when a bet is actually dead.
The disconfirming observation in step 1 is what tells you that, and it has to be written down
before you are emotionally invested in the answer.
