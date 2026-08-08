# Average is not good enough
### Notes on Max Hodak's YC Startup School 2026 talk

Speaker: Max Hodak, CEO of Science Corporation.
Event: YC Startup School 2026.
Video: https://www.youtube.com/watch?v=Xc4klGbq8v8
Transcript source: https://www.ycrootaccess.com/p/max-hodak-there-are-no-blanket-rules

A note on the title. YC's own Root Access publication files this session as "How to Build
a Startup That Moves Fast." The phrase "average is not good enough" comes from the
judgment section near the end, where he argues that copying your neighbors pulls you
toward the class mean. Both titles describe real halves of the talk. The talk itself is
mostly about company plumbing, and the judgment argument is the coda.

---

## Who he is and why the talk is shaped this way

Hodak has been working on brain-computer interfaces for close to twenty years, starting
as an undergraduate at Duke. He spent five years at Neuralink, which he co-founded, and
left in 2021 to start Science with several ex-Neuralink colleagues.

That background matters for reading the talk. He is not a software founder giving generic
startup advice. He runs a company that buys argon and xylene in bulk, fabricates wafers,
runs clinical trials in multiple countries, and answers to medical device regulators. Most
of his advice is calibrated to that: capital-intensive, physically constrained, slow
feedback loops. He says so explicitly, and then partly undercuts it by claiming the
infrastructure lessons generalize across deep tech.

## What Science actually built

The product is a retinal prosthesis for people who have lost photoreceptors. A chip goes
under the retina and acts as a solar cell. The patient wears glasses carrying a camera and
a laser projector, which beams the image onto the implant, which stimulates the surviving
retinal tissue directly. Dead photoreceptors are bypassed rather than repaired.

Concrete results he cites:

- Three clinical trials completed, spanning six countries.
- Results published in the New England Journal of Medicine.
- Approved as a medical device in Europe.
- One patient read a 300-page novel using the device.

The 300-page novel is the anecdote he leads with, and it is the strongest thing in the
talk in terms of verifiable claims. Independent reporting in March 2026 covers a $230M
raise and a pending FDA decision, though he does not give that number on stage.

## The thesis: speed is a function of infrastructure

His central claim is that startups rarely die from technology. They die from
organizational execution. The variable that decides which side you land on is the rate of
iteration, and the rate of iteration is set by boring internal systems rather than by
technical brilliance.

The compounding argument: a team that completes a learning cycle weekly against a team
that completes one monthly is not 4x faster. Over a few years the gap becomes
unrecoverable, because each cycle informs the next. He applies this to rockets, cars,
drugs, and BCIs alike.

He borrows the military line that amateurs talk strategy and professionals talk logistics,
and uses it to justify spending the bulk of a Startup School slot on purchase orders and
performance reviews.

He calls the collection of purchasing, accounting, recruiting, performance review,
budgeting, safety, and quality the company's operating system. His claim is that getting
these right early makes everything downstream cheaper, and getting them wrong means
spending $5M a month with very little control over what that money is doing.

## Purchasing, and why founder approval is a tax

The failure mode he describes is founder-level sign-off on every purchase. A founder
approving a $3,000 order is spending expensive attention on a decision that carries almost
no information. Worse, it puts a queue in front of every experiment.

The fix he describes is not a rule but a structure: give departments real budgets and real
spending authority, cap monthly burn at the level that actually matters, and stop
reviewing individual transactions. The employee closest to the experiment has the context
to make the trade-off, provided they can see the resource constraint they are working
inside.

He is blunt about how slow commercial procurement is in practice. Setting up a new vendor
involves quotes, purchase orders, invoices, and certificates of insurance, and typically
takes about two weeks before anything can be ordered. He describes procurement as a living
organism that needs metrics and active management, not a system you configure once.

Science built internal software called Helix to automate purchasing.

## Cost attribution, and why experiments look free

This is the most specific operational problem he raises and the one least likely to occur
to a software founder.

When you buy materials in bulk (argon, nitrogen, xylene, resins, cell culture media), the
money leaves the company at purchase time and sits on the books as inventory. When a
scientist later runs an experiment consuming some of that inventory, the experiment
appears to cost nothing. Nobody is lying. The accounting simply does not connect the
purchase to the use.

The consequence is that experiment scoping becomes untethered from budget. Science built
spreadsheets that estimate a real internal price per unit, including rent, tool
depreciation, and assumptions about future volume, then wired purchasing into their
manufacturing database so consumption could be correlated back to cost.

The number he gives to make this vivid: each wafer iteration costs about $40,000.

He then walks the arithmetic of a hypothetical Series A to show why $40,000 is a lot:

- Raise $20M, plan for four years, roughly 20 employees.
- About half the burn is headcount, on the order of $3M a year.
- Facilities run $750K to $1M a year (roughly 20,000 sq ft at about $4 per sq ft per month).
- What is left is around $3M a year of actual research budget.

At $40,000 per wafer iteration, $3M a year is a countable number of attempts. That is the
point of the exercise: if you cannot see the cost, you cannot plan the number of shots you
get.

## Hiring as a four-stage funnel

He argues you need at least four distinct stages to get enough signal, and describes
Science's.

**Stage 1, company-wide voting on applications.** Each application is routed to roughly
seven or eight employees whose backgrounds match the applicant. They vote. Turnaround is
24 to 48 hours. About 17% advance. This runs on internal software they built.

**Stage 2, phone screen.** Screeners are drawn from a company-wide pool rather than a
dedicated recruiting team. They score three things:

- Judgment, meaning decision quality under ambiguity.
- Horsepower, meaning raw technical capability.
- Agency, meaning whether the person actually executes on their own ambitions.

**Stage 3, homework.** He wants take-homes that resist AI completion, have a high ceiling
so strong candidates can separate themselves, and reduce naturally to two or three
scorable metrics. He points to Anthropic's GPU kernel optimization exercises as the model:
the task has an objective score, and a better answer is visibly better.

**Stage 4, onsite interviews.** He targets at least 25% conversion from onsite to offer.
Below that, you are burning employee days on candidates who were never going to make it,
and the earlier stages are miscalibrated.

## Eigen reviews

The most idiosyncratic thing in the talk, and the part most likely to be either genuinely
useful or a governance hazard depending on the company.

His complaint about annual 360 reviews is that they are disruptive, slow, and mostly
surface problems everyone already knew about. They add latency to information that was
available months earlier.

Science replaced them with what he calls Eigen reviews:

- Runs every four to six weeks, continuously rather than as an annual event.
- Company-wide voting on one question: knowing how this person turned out, would you vote
  to hire them again today?
- Five response categories: known good, strong yes, yes, no, strong no.
- Votes are weighted by eigenvector centrality, the same family of algorithm as PageRank.
  Your vote counts for more if people whom well-regarded colleagues rate highly also rate
  you highly. Credibility is recursive.
- Collusion detection uses Markov chain Monte Carlo dropout: randomly delete edges in the
  voting graph across about 1,000 iterations and look at the distribution of resulting
  scores. A single peak means the score is robust. Multiple peaks mean a bloc is holding
  someone up or pushing someone down, and a human goes and looks.

Feedback lag drops to roughly a month. He presents this as removing the traumatic annual
HR cycle rather than as a surveillance mechanism, which is the obvious counter-reading and
which he does not address.

## Build the software yourself

He notes that essentially nobody likes their ERP or their applicant tracking system.
Commercial tools encode someone else's process, and the mismatch is where the friction
lives.

His examples of companies that built their own: Science with Helix, YC with its internal
tooling, Facebook, and SpaceX and Tesla with Warp Speed. His claim is that these systems
produce a measurable efficiency advantage because they encode the founder's actual
judgment about how the company should work.

The reason this is newly available: the cost of writing custom internal software has
collapsed. He frames this as his contrarian belief, and is honest that it still sounds bad
out loud. If you raise a Series A and tell your board you plan to vibe code a purchasing
system, he expects any reasonable board to ask what you are thinking.

## Judgment cannot be delegated, and average is not good enough

The coda, and the source of the title given to this talk.

His framing is a school analogy. Copying off your neighbors moves your grade toward the
class average. In school that is often a winning strategy. In startups it is not, because
the outcomes that matter live in the long tail, and the average outcome is failure.

Two consequences he draws:

First, you cannot delegate judgment. You can delegate purchasing, screening, scheduling,
and most execution. The decision that only you can make is the one where the stakes are
highest and, he says, there is nobody to ask. Several years into a company, the important
decisions are specific enough to your situation that no advisor has seen the fact pattern.

Second, being right often feels like being alone. If your view is the same as everyone
else's, you are producing the average result.

He generalizes this into a rejection of startup advice as a genre: there is no set of five
bullet points you can crank to produce a successful company. He repeats it as "there are
no blanket rules in startups." Each fact pattern is different, and the work is developing
judgment tuned to your own domain rather than importing someone else's heuristics.

## Action produces information

A smaller idea he keeps returning to. He borrows the physics intuition that acting on a
system generates entropy, and therefore information. When you are stuck and constrained,
taking action is how you find out what your options actually are.

The example he gives is uncomfortable and specific: removing a strong individual
contributor who is misaligned with the company's current phase can unlock the company and
let it move into a new phase, even when that person is genuinely capable. The action
itself reveals what was being blocked.

## Fundraising for something that takes years

His formula, such as it is:

1. Work out what it actually costs to run the experiments that reach your next value
   inflection point. Not the full company vision. The next real milestone.
2. Raise twice that.
3. Assume waste. He calls 20% to 30% waste a pretty good outcome, not a failure.

The reasoning behind the 2x is that founders ask for what feels polite rather than what
the experiment costs, then spend the round dying slowly and starting the next raise too
early. He calls the perpetual raising cycle money cancer.

He also argues for pushing toward revenue and sustainability earlier than instinct
suggests, including in deep tech. Once a company is not dependent on the next round, the
valuation conversation shifts from probability of survival to the long-term roadmap, which
is a much better conversation to be having.

## Q&A, the parts worth keeping

**Academia versus industry.** His model is that when a field starts working, the best
talent migrates to industry. Computer science was CMU and Harvard twenty years ago and is
now Google, Apple, and OpenAI. Rocket engines were NASA and universities and are now
SpaceX and Blue Origin. Life sciences is the exception he names, still heavily academic,
because pharma is weak at discovery. His advice: if the field has moved, work at a
high-performing company rather than doing a PhD.

**Evidence of exceptional ability.** Credentials are weak signal because they are shared
with your whole cohort. He prefers legible competitive games with real outcomes: chess
grandmaster, Design/Build/Fly, Formula SAE. He claims a striking number of Silicon Valley
deep tech companies were built by Formula SAE alumni, on the theory that those people spent
college building things, racing them, and finding out. He recommends entering through one
hard skill (software, electronics, mechanical, materials) and adding breadth after.

**AI in scientific work.** Three places it has changed things at Science: coding, where he
says code review needs are much reduced; regulatory and standards compliance, where
identifying applicable standards and generating evidence tables used to take many months;
and general team amplification. He is explicit that agents multiply a team rather than
replace it.

**Hardest remaining BCI problem.** Materials science, specifically biocompatible conformal
packaging that survives long-term implantation. Power and thermal budgets drive most of the
implant design trade-offs.

**Consciousness.** He treats it as an eventual experimental question rather than a
philosophical one: a device with full visibility into neuronal state could test claims
about consciousness directly, and it would have to be tested in humans. Current implants
are not built for this. He puts it far down the roadmap.

**Interdisciplinary structure.** He prefers small teams that hold the whole problem in
their heads over large centers organized as verticals that meet in the middle. His example:
protein engineering produced opsins requiring less light, which relaxed the constraints on
the electronics. Nobody working inside a single vertical finds that trade.

**Culture.** He describes Science as roughly 30% transhumanist mission people and 70%
serious clinicians and researchers, and argues you need both. The first group makes the
company willing to attempt something implausible. The second group makes the clinical
trials real.

**Neuralink.** What he says he took from it was watching someone with empirically good
judgment make hard calls, and later finding out those calls were right. He frames it as
calibrating instincts against concrete outcomes rather than absorbing advice.

**Best advice received.** He declines the question, saying he has too little memory left
after twenty years to pick one. The closest he gets is his own thesis back: speed is the
basis of success, infrastructure determines speed, and there are no general principles.

---

## What is genuinely actionable

Ordered by how likely it is to survive contact with a company that is not Science.

1. **Instrument the cost of one repeated unit of work.** Pick the thing your team does
   over and over (an experiment, a test run, a customer onboarding) and compute what it
   actually costs including overhead. If the number surprises you, your scoping decisions
   have been running blind.
2. **Replace transaction approval with budgets and a burn cap.** If a founder is approving
   individual purchases, the queue is the cost, not the money.
3. **Measure onsite-to-offer conversion.** If it is well under 25%, the problem is
   upstream, and the fix is in screening, not in the interviews.
4. **Rebuild take-homes to be objectively scorable.** A task that reduces to two or three
   metrics with a high ceiling separates candidates. A task that reduces to a yes-or-no
   judgment mostly measures the reviewer.
5. **Shorten the feedback interval on people.** The specific eigenvector machinery is
   optional. The claim that survives without it is that annual review cycles put a
   twelve-month lag on information available in six weeks.
6. **Size the raise to the next inflection point, then double it.** And budget for 20% to
   30% waste rather than pretending it will not happen.
7. **Check what internal tooling you are renting out of habit.** The cost of building has
   moved. Some of what you buy no longer clears the bar.

## Where he is talking his own book, or cannot be checked

- **The infrastructure thesis is unfalsifiable as stated.** "Companies fail on execution,
  not technology" is compatible with almost any outcome, because a failed company can
  always be described as having executed poorly. He offers no case where good
  infrastructure failed to help or where a company won despite bad plumbing.
- **Eigen reviews have no reported results.** He describes the mechanism in detail and
  reports no outcome data: no retention comparison, no evidence that scores predict
  anything, no accounting for how many collusion flags turned out to be real. The clique
  detection is presented as a solved problem when it is a mitigation with unknown recall.
  Weighting votes by peer credibility also concentrates influence in whoever is already
  central, which is a known property of PageRank-style algorithms and is not discussed.
- **Build-your-own-software is his contrarian position and also his product story.** He
  built Helix and is arguing that building Helix was correct. He acknowledges a board would
  push back, then does not engage with the strongest version of the pushback, which is
  maintenance burden and key-person risk on systems nobody outside the company understands.
- **The Formula SAE claim is unsourced.** "A striking number of deep tech founders did
  Formula SAE" is the kind of pattern that survives because it is memorable. No numbers,
  and heavy survivorship exposure.
- **The 17% and 25% numbers are Science's, at Science's scale.** They are useful as a
  demonstration that someone measures these things. They are not benchmarks.
- **Speed as the master variable is convenient for a founder in a slow industry.** Medical
  devices are gated by trial enrollment, regulatory review, and biology. A thesis that
  says internal velocity is the lever is a thesis that makes the controllable part feel
  decisive.
- **"There are no blanket rules" is itself delivered as a blanket rule,** immediately after
  forty minutes of rules about purchasing, hiring, and reviews. Worth holding both: the
  operational specifics are the useful content, and his own framing tells you to test them
  rather than adopt them.
- **Unverified from this source:** the $230M raise and FDA status appear in press coverage
  from March 2026, not in the talk. The claim about SpaceX and Tesla's Warp Speed
  efficiency advantage is asserted without evidence. The regulatory compliance time savings
  from AI are described qualitatively with no before-and-after numbers beyond "many
  months."
