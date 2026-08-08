---
name: company-operating-system-method
description: Method for raising a company's iteration rate by fixing its internal systems (purchasing, cost attribution, hiring, performance review, budgeting) rather than its strategy. Use when a team is moving slowly and nobody can say why; when a founder is approving individual purchases; when experiment or project scoping ignores real cost; when a hiring funnel wastes onsite time; when annual review cycles are the only feedback signal; when sizing a fundraise for a long-horizon technical milestone; or when deciding whether to buy internal tooling or build it. Derived from Max Hodak's YC Startup School 2026 talk.
---

# Company operating system method

Source: Max Hodak (CEO, Science Corporation; previously co-founder of Neuralink), YC Startup School 2026, "Average Is Not Good Enough." Video: https://www.youtube.com/watch?v=Xc4klGbq8v8

The premise: startups rarely die from technology, they die from execution, and execution
speed is set by internal plumbing rather than by talent or strategy. Treat these as
defaults to test, not rules. Hodak's own closing position is that there are no blanket
rules, which applies to this file too.

## The one-line version

Find whatever adds latency between deciding to try something and finding out the result,
remove it, and keep the one decision you cannot delegate.

## 1. Diagnose latency, not effort

When a team is slow, do not start with headcount or motivation. Trace one complete
learning cycle end to end and time each hop: wanting a material to having it, a candidate
applying to a decision, someone underperforming to that person hearing about it, running
an experiment to knowing what it cost.

The compounding argument justifies the exercise. A team completing a cycle weekly against
one completing it monthly does not end up 4x ahead, it ends up somewhere the slower team
cannot reach, because each cycle informs the next. Purchasing, accounting, recruiting,
performance review, budgeting, safety, and quality are the company's operating system, and
slowness lives there more often than in the work itself.

## 2. Replace approval with budget

Founder sign-off on individual purchases is the canonical case. A founder approving a
$3,000 order spends expensive attention on a low-information decision and puts a queue in
front of every experiment downstream.

The replacement: give each team a real budget and real spending authority, cap monthly burn
at the level that actually threatens the company, and stop reviewing transactions. Make
sure whoever is spending can see the constraint they are inside. Authority without
visibility into remaining resources produces worse decisions, not faster ones.

Expect procurement to stay slow regardless. New vendors need quotes, purchase orders,
invoices, and certificates of insurance, which runs about two weeks before anything ships.
Measure that lead time continuously rather than configuring the system once.

## 3. Make the cost of a repeated unit visible

The trap: materials bought in bulk leave the bank account at purchase time and sit as
inventory, so when someone later consumes them the experiment appears free. Nobody is
lying, the accounting just does not connect purchase to use.

Pick the unit of work your team repeats (an experiment, a build, a test run, an
onboarding) and compute a real internal price for it, including rent, depreciation, and
volume assumptions. Wire the purchasing record to whatever records consumption. Then
divide.

Hodak's worked example: a wafer iteration runs about $40,000, and a $20M Series A over
four years leaves roughly $3M a year of research budget after headcount (about $3M a year
for 20 people) and facilities ($750K to $1M a year). The output is a shot count. If a team
cannot say how many attempts its runway buys, scoping is happening blind.

## 4. Hire through at least four stages, and measure the last one

Fewer than four stages does not produce enough signal. A working shape:

- **Application review by distributed vote.** Route each application to seven or eight
  employees whose background matches the applicant, with 24 to 48 hour turnaround. At
  Science about 17% advance.
- **Phone screen from a company-wide pool**, not a dedicated recruiting team, scoring
  judgment (decision quality under ambiguity), horsepower (raw capability), and agency
  (whether they execute their own ambitions).
- **Homework that resists AI completion**, has a high ceiling so strong candidates can
  separate, and reduces to two or three objective metrics. Think optimization task with a
  score, where a better answer is visibly better.
- **Onsite**, held to at least 25% conversion to offer.

Use the last number as the diagnostic. Well under 25% means the earlier stages are
miscalibrated and you are burning employee days. Fix screening, not interviews.

## 5. Shorten the feedback interval on people

Annual 360 reviews are slow, disruptive, and mostly restate what everyone already knew.
Their real cost is putting a twelve-month lag on information that existed in six weeks.

Science's version, called Eigen reviews, runs every four to six weeks and asks the whole
company one question: knowing how this person turned out, would you vote to hire them
again today? Five options, from known good through strong no. Votes are weighted by
eigenvector centrality (the PageRank family), so credibility is recursive. Collusion is
checked by Markov chain Monte Carlo dropout: delete graph edges at random across about
1,000 iterations, and read multiple peaks in the score distribution as a voting bloc worth
investigating.

If you adopt one part, adopt the interval. The eigenvector machinery is optional and
carries a cost: weighting by peer credibility concentrates influence in whoever is already
central, and the dropout check is a mitigation with unknown recall, not a solution.

## 6. Consider building the tooling

Nobody likes their ERP or their applicant tracking system, because commercial software
encodes someone else's process and the mismatch is where friction lives. Companies that
built their own include Science (Helix, for purchasing), YC, Facebook, and SpaceX and
Tesla (Warp Speed). What changed is the cost of writing custom internal software, so old
buy decisions are worth re-checking.

Hold the counterargument alongside it. Hodak frames this as his contrarian belief and
concedes a board would fairly question a plan to vibe code a purchasing system. The risks
he skips are maintenance burden and key-person dependency. Build where the process is
genuinely yours, buy where it is a commodity.

## 7. Size the raise to the next inflection point

Compute what it costs to run the experiments that reach the next real value inflection
point, not the full company vision. Raise twice that. Budget for waste, where 20% to 30%
is a good outcome rather than a failure.

The 2x exists because founders ask for what feels reasonable rather than what the
experiment costs, then spend the round dying slowly and starting the next raise early.
Push toward revenue sooner than instinct suggests, including in deep tech: once the next
round is not survival, the valuation conversation becomes about the roadmap instead.

## 8. Keep judgment, delegate everything else

Copying your neighbors moves you toward the class average. In school that works. In
startups the average outcome is failure, so anything that pulls you toward consensus pulls
you toward the mean of a distribution you need the tail of.

Delegate purchasing, screening, scheduling, and most execution aggressively. Do not
delegate the judgment call at the top. Several years in, the decisions that matter are
specific enough that no advisor has seen your fact pattern.

When stuck, act. Acting on a system produces information about it. Hodak's example is
removing a capable individual contributor misaligned with the company's current phase,
which can unlock a transition that analysis alone would not have revealed.

## Checklist

- [ ] Time one full learning cycle hop by hop. Write down where the days go.
- [ ] Find every place a founder approves a transaction. Replace with a budget and a burn cap.
- [ ] Price your most-repeated unit of work, then convert runway into a shot count.
- [ ] Measure onsite-to-offer conversion. If under 25%, fix screening.
- [ ] Cut the people-feedback interval to roughly monthly before touching any algorithm.
- [ ] Re-check one build-versus-buy call on internal tooling.
- [ ] Name the one decision this quarter you are not allowed to delegate.

## What this method does not settle

The claim that companies fail on execution rather than technology is hard to falsify, since
any failure can be relabeled poor execution after the fact. The Eigen review system comes
with no outcome data attached. And a thesis that internal velocity is the master variable
is convenient for a founder in an industry gated by trial enrollment and regulatory review.
Run these against a real company before adopting them, which is what the source recommends
anyway.
