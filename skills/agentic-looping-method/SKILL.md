---
name: agentic-looping-method
description: Method for scaling token spend against a single outcome inside a continuous feedback loop, and for choosing the metric that makes an agent swarm productive instead of expensive noise. Use when deciding whether a task is worth pointing many agents at, when an agent swarm is producing volume without progress, when identifying which repeated business process to automate, or when someone asks how to get leverage beyond a single agent session. Derived from Alexandr Wang's YC Startup School 2026 talk.
---

# Agentic looping method

Source: Alexandr Wang (Meta Superintelligence Labs, founder of Scale AI), YC Startup School 2026, "This Is a Once-in-a-Civilization Opportunity." Video: https://www.youtube.com/watch?v=sJ4VJWycX9M

## The claim

Asked what people are missing right now, Wang's answer was agentic looping. Specifically: there is large unclaimed opportunity in building systems that let you spend 1000x or even 1,000,000x more tokens driving a single outcome inside a continuous feedback loop.

Most people run an agent once and stop. The opportunity is in the loop, not the run.

## Find the loops

His model of a company is a large-scale feedback loop with humans operating each edge. Get customers, make them happier, they spend more, you hire more people, who get more customers. Inside that outer loop sit many smaller loops.

The work is building agentic systems that operate and optimize those inner loops.

To apply this, do not start from "what could an agent do." Start by drawing the repeating cycle in your business or project and asking which edge a human is currently walking that a loop could walk instead.

## The metric is the whole thing

The condition Wang attaches is not optional and it is where most attempts fail.

With the right agentic loop and the right eval or metric for agents to optimize, a swarm can accomplish more than a team of 100 engineers, and do it easily. Without that metric you have expensive noise. Volume of agent output is not progress.

So the order of operations is:

1. Define the metric or eval first.
2. Build the loop around it.
3. Only then scale the token spend.

Reversing that order produces impressive-looking activity and no result.

This converges with the verification argument from the Claude Code side of the same event, arrived at independently. Anthropic frames it as ground truth from the environment; Wang frames it as the metric agents optimize. Same constraint, different vocabulary.

## The mechanics are mundane

Wang was asked directly whether it really comes down to markdown files and cron jobs. He confirmed it. His list: figure out the metric, then skills, markdown files, cron jobs, and a goal command.

His own comment was that it is always funny how mundane everything is once you dig in.

Practical implication: do not wait for better tooling. The stack that produces this leverage already exists and is unglamorous. If you are searching for a technique you are missing, you probably are not missing one.

His stated advice when the topic of magic techniques came up was to ignore LinkedIn.

## Cost is a design constraint, not a line item

If the strategy is spending 1000x more tokens per outcome, price per token stops being procurement detail and becomes the thing that decides whether the loop closes at all.

When designing a loop, cost the inner iteration before building it. A loop that is correct but unaffordable per iteration is not a loop. Consider cheaper models for high-volume mechanical steps and reserve expensive ones for the steps that need judgment.

Note when weighing this: Wang sells a low-cost frontier model, so he has an interest in the argument. The logic holds independent of who makes it.

## Where the leverage sits

Wang's view is that the bottleneck is not model progress but diffusion, meaning getting the technology through the rest of the world. If models froze today there would still be decades of upheaval in how the economy operates.

He also argues the competitive shape changed. Starting a company used to be David against Goliath, requiring cleverness and an angle because you had fewer resources. With agents it is closer to Goliath against Goliath, with the startup as the amplified side.

His prediction for what will look obvious in hindsight: intelligence became abundant and agency became abundant. For all of prior history, coordinating groups of smart people toward a shared goal was the bottleneck on progress. When that stops being scarce, vision and ambition become the scarce inputs instead.

## The disagreement worth knowing

Wang sits on the accumulate-scaffolding side of a live split. He describes the method as building skills, markdown files, and cron jobs around a metric. Garry Tan argues the same direction more strongly. Boris Cherny argues close to the opposite, that you should delete accumulated instruction files on every model release and add back only what you observe the model failing without.

All three agree the feedback signal is what makes the loop work. They disagree about how much written structure should surround it. Test it on your own work rather than picking a side.
