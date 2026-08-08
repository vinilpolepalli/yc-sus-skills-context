---
name: ambition-sizing-method
description: Method for choosing how large a bet to make at the start, testing an idea against the life it creates if it works, and keeping a real feedback loop through a long build. Use when deciding between a narrow MVP and an ambitious first version, when a build will take many months before public launch, when the chosen niche looks crowded with teams running the same iterate-outward strategy, when someone asks whether lean startup still applies in the AI era, or before raising capital that commits you to a decade. Derived from Patrick Collison's YC Startup School 2026 talk.
---

# Ambition sizing method

Source: Patrick Collison (Stripe), YC Startup School 2026, "What If You Succeed?", interviewed by Harj Taggar. Video: https://www.youtube.com/watch?v=5d6y3poKwK4

The argument is not that lean startup was wrong. It is that lean startup was a response to a capital constraint that has partly lifted, and that the feedback discipline inside it should survive the change while the scope discipline should not.

## The one-line version

Size the first bet to what the opportunity deserves rather than to what you can afford, check that you want the outcome before you chase it, and get a real user on a real transaction inside two months no matter how long the build is.

## 1. Separate the two halves of lean startup

Lean startup bundles two things that are usually treated as one:

- Small initial scope. Build the minimum slice, find a niche, buy ads against it, expand outward.
- Tight feedback. Never build on internal assumptions, always be reading real user behavior.

The first was largely a budget constraint. Building a large surface was expensive, so you could not start wide. That constraint is weaker now: spinning up many capabilities at once is much cheaper.

The second was never a budget constraint. It is still correct.

When someone says AI breaks the lean playbook, check which half they mean. If they are using it to justify skipping feedback, they have the argument backwards.

## 2. Test whether your niche is already tilled

The niche-and-iterate search is now crowded. Many teams with the same tools run the same incremental search over the same obvious adjacencies, and the space gets exhausted quickly.

The test: would a hundred other competent teams, handed your tools and your market, pick the adjacency you picked?

If yes, the response is to de-correlate, not to move faster. Faster execution inside a heavily searched space produces a race you win on margin rather than on position.

Counterexamples worth holding in mind: the frontier labs and Anduril both started with a large, expensive, unhedged bet rather than a minimum viable slice. Both are cited in the talk as anti-lean and successful.

Hold the counter-caveat too. Those are survivors from a category whose failures are expensive and invisible. No base rate was offered, and you should not assume one.

## 3. Ask the success-conditional question

Before raising significant capital, stop asking "is this a good idea" and ask "what if you succeed?"

Concretely: given that this works, do you want to be doing it in year ten? Year seventeen? Year thirty?

Most idea evaluation optimizes the probability of success. This optimizes the conditional. They are different questions and the second one is cheaper to answer, because it depends on your own preferences rather than on the market.

Practical form when advising or self-checking:

1. Write down what the company looks like at 10x its target scale.
2. Write down what your week looks like in that company.
3. Ask whether you would take that week if it were offered today as a job.
4. If the answer is no, the upside case is the problem, not the downside case.

Schlep blindness is the related trap, and the fix is not "embrace the schleps." It is checking whether the schleps come attached to something you find genuinely interesting. Stripe's version: the payments arcana is dull, the fact that every customer is an applied theory of how some part of the world works is not.

## 4. Long build, early user

The rule that makes an ambitious scope safe.

If your product has genuine infrastructure preconditions (regulatory, financial, safety-critical, partnership-dependent), delaying the public launch is defensible. You cannot iterate your way to a banking partner.

What is not defensible is delaying the first real user.

The Stripe pattern, with dates, because the dates are the falsifiable part:

- Started fall 2009.
- First live production user January 2010, roughly two months in: Ross Boucher at 280 North. He could do exactly one thing, charge a card.
- Everything built after that was pulled by what that user and the ones after him asked for next: dashboards, then refunds, then payouts. Just-in-time development.
- Beta users grew every month from there.
- Public launch September 2011, about two years after starting.

So: two years without a public launch, not two years without feedback.

Apply it as a check rather than a story. If you are eighteen months into a build and cannot name a user doing a real transaction from month two, you are not running this play, you are running a different one that happens to share a timeline.

## 5. Look for opportunities protected by a status filter

Stripe's problem was obvious to every developer who had tried to take a payment. It sat there anyway, because two young founders starting a financial services company read as absurd and fintech did not exist as a category.

The general shape: an opportunity that is technically legible to practitioners and socially illegible to everyone whose approval you would normally seek.

This is a stronger filter than "solve a real problem," because it explains why the problem is still available. When an obvious idea is unclaimed, look for what is keeping serious people away. If the answer is a technical wall, be careful. If the answer is that it looks unserious, that is the interesting case.

## 6. Do not assume the incumbent takes everything

The structural argument against the hegemony fear is about organizational capacity rather than model capability. Large organizations, however capable, are bad at aggressively pursuing a hundred priorities at once. Companies that looked omnipotent twenty years ago ceded ground anyway.

Labs specifically tend to expand scope ambitiously, and broad scope expansion opens gaps rather than closing them. A company chasing everything defends nothing in particular.

This is not a claim that you will beat them at their center. It is a claim about the residual, and the residual is where you should be looking.

## 7. Reconsider the enterprise sales timeline

The claim, from Stripe's vantage: enterprises are far more willing to buy from startups than they used to be, because the perceived risk of the status quo is now higher than the risk of an unproven vendor. Buyers are adopting at meaningful scale immediately instead of piloting for a year.

If you shelved enterprise sales because the cycle was too long for your runway, that assumption is worth retesting this quarter. It is cheap to falsify: a handful of outbound conversations will tell you whether the urgency is real in your category.

## 8. Keep knowledge in cache

Applies to you and to how you configure agents.

Knowledge you hold directly supports far more reasoning round trips per minute than knowledge you have to fetch. Asking an agent to look something up is much slower than knowing it. The revealed-preference check: companies still pay a large premium for raw cognitive ability, so the value of knowing things has not collapsed.

The operational version: do not stop learning a domain because you can retrieve it. Retrieval costs a round trip, and round trips are the budget when you are reasoning about something hard.

## 9. Refuse to forecast

Collison declined to predict twice. His example: aviation was genuinely important and did not reshape society the way people said it would.

Treat every claim in this file as an observation about the present rather than a trend line. The decentralization thesis and the business-formation data are both readings of now, offered by someone who explicitly refused to extend them forward. Do the same.

## Checklist

- [ ] Name the adjacency you picked. Ask whether a hundred similar teams would pick it too.
- [ ] Write the year-ten week. Decide whether you would take it as a job today.
- [ ] Put a date on the first real user. If it is more than two months out, say why in one sentence and check whether that sentence is a genuine precondition or an excuse.
- [ ] Identify what keeps serious people away from your idea. Technical wall or status filter.
- [ ] Retest one assumption you inherited from the capital-constrained era: initial scope, sales cycle length, or hiring pace.

## What this method does not license

Scope up is not launch late. Stripe ran ambitious scope and a live user at month two simultaneously, and the second is what made the first survivable. Any reading of this file that drops the feedback loop has taken the permission and left the discipline.

Also note the source of the underlying data. The business-formation numbers, the median-business improvement, and the enterprise-buying shift are all Stripe's internal view, characterized verbally on stage, over a population that skews online and developer-adjacent. Directionally useful, not a measurement of the economy.
