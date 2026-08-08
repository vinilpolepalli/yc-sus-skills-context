# Patrick Collison at YC Startup School 2026

Interviewed by Harj Taggar, Center Court session, Chase Center, San Francisco, Sunday 26 July 2026.
Video: https://www.youtube.com/watch?v=5d6y3poKwK4

A note on the title. The published transcript and most write-ups title this session "What If You Succeed?" The framing "Is AI breaking the lean startup playbook?" is one thread inside it, and it is the thread Harj pushes hardest on, but it is not the whole conversation. Both labels point at the same 40-odd minutes.

Source used: the Root Access transcript at https://www.ycrootaccess.com/p/patrick-collison-what-if-you-succeed, cross-checked against a set of independent session notes at https://github.com/Princeu3/yc-startup-school-2026-notes. Where the two disagree I say so.

## Who is on stage and why it matters

Harj opens by noting the two of them met about 20 years ago and started a company together. That is Auctomatic, the YC-backed company Harj, his cousin Kulveer, and the Collison brothers built in 2007 and sold in 2008. So this is not a journalist interviewing a CEO. It is a former co-founder who knows where the bodies are, which is why the questions land harder than they would at a normal fireside.

Collison's pre-Stripe credential that comes up early: Croma, a Lisp dialect he wrote in secondary school. Relevant later, because his position on learning is not abstract.

## Cognitive L1 cache

Harj asks the obvious 2026 question: with models this good, what is still worth learning?

Collison reaches for Jeff Dean's "numbers every engineer should know," the latency table you keep in your head so you can reason about a system without going and measuring it. His argument is that general knowledge behaves the same way. You can ask an agent to look something up, and it will. But the number of round trips you get per minute inside your own head is far higher than the number you get through a prompt and a tool call.

The phrasing from the captions: asking an agent to fetch something is "a hell of a lot slower than knowing it in cognitive L1 cache."

He backs it with a revealed-preference argument rather than a sentiment: companies still pay an enormous premium for raw cognitive ability. If the value of knowing things had actually collapsed, the labor market would have noticed. His conclusion is conservative rather than triumphant. Do not renounce learning until there is evidence the benefit has saturated.

He puts writing and interpersonal communication in the same bucket. He says he does not use models to write for him, and describes them as still deficient at the interpersonal register, even granting everything else they can do. Worth noting this is a stated personal practice from someone whose company sells AI-adjacent infrastructure, not a measured claim.

Scheduling coincidence the notes flag: Jeff Dean spoke on the same stage the day before.

## Dropping out, twice, and why that was the wrong frame

Collison dropped out of MIT as a freshman for Auctomatic, went back for roughly a year, then left again for Stripe.

The takeaway he draws is the inverse of the usual founder mythology. Dropping out is reversible. You can go back, he did. And as far as he can tell, nobody has ever cared whether a founder finished the degree. He characterizes the reputational risk as de minimis in both directions: leaving costs you nothing, and staying costs you nothing either.

He is explicit that he felt real urgency at the time, and that in hindsight the framing of startups as something you must abandon school for was a poor one. If you like college, finish it. If you are not captivated, leaving is cheap. The urgency was manufactured.

This is a small answer with a large implication for the rest of the talk: he is consistently skeptical of advice that is really just social pressure wearing a strategy costume.

## Stripe's origin, which began at this same event

He and John attended Startup School in 2009. They got sushi in Potrero afterward and decided to start Stripe on the walk back. His memory of the reasoning, roughly: we might as well, it probably will not be that hard.

His own gloss on the story is two-part and mostly a joke: go get sushi in Potrero tonight, and beware of yak shaves.

Discrepancy to flag. The Root Access transcript and the derivative write-ups place Startup School 2009 in Berkeley. The independent session notes say Burbank. Startup School 2009 was held at UC Berkeley, so Berkeley is the likelier reading and the Burbank mention is probably a transcription artifact. Not load-bearing either way.

## Why Stripe worked, in his telling

Harj asks the causal question directly. Collison's answer is unfashionably plain: a concrete, easy to explain customer problem. Accepting payments online in 2010 was genuinely painful and every developer who had tried it knew it.

The interesting half of the answer is why an obvious idea sat there. He says nobody took it seriously. Two young founders starting a financial services company read as absurd at the time. Fintech did not exist as a sector or a word. The idea was legible to developers and illegible to everyone whose approval you would normally need.

That is the actual mechanism worth extracting, and it is stronger than "solve a real problem." The opportunity was protected by a status filter rather than a technical one.

## The two-year build, and the production user that saved it

This is where Harj starts pushing, because it contradicts YC's own doctrine.

Facts. Stripe started in fall 2009. Public launch was September 2011. That is roughly two years of building before anyone could sign up.

Collison's defense is that payments has hard preconditions. Banking partners, security, money movement mechanics, compliance, and a real liability surface. You cannot scale the experience without those in place, and there is no version of the product where you skip them and iterate your way there later.

The part that keeps this from being a self-serving story: they were not building in the dark. The first live production user arrived in January 2010, about two months in. That was Ross Boucher at 280 North. He could do exactly one thing: charge a card. Everything after that was pulled by what Boucher and the users who followed him asked for next. Dashboards, then refunds, then payouts. Collison calls it just-in-time development.

Beta users grew every month from January 2010 through the September 2011 launch. So the two years were not two years without feedback. They were two years without a public launch, which is a different thing.

The rule that falls out of this, and he states a version of it: if you have genuine infrastructure dependencies, delaying the public launch is defensible. Getting a real user doing a real transaction is not optional and should happen in the first couple of months.

Skeptical note. "Genuine infrastructure dependencies" is doing a lot of work and is exactly the phrase a founder will use to justify eighteen months of not shipping. The January 2010 date is the falsifiable part of the story. If you are running the same play and you do not have a live user two months in, you are not running the same play.

## Is the lean startup playbook still right

The titular exchange. Harj asks whether AI changes the calculus on ambition: still narrow and focused at launch, or ambitious from day one?

Collison does not claim lean startup was wrong. He argues its preconditions have moved.

What he says has changed:

Twenty years ago, capital constraints made the lean approach close to mandatory. You could not afford to build a large surface. You found a niche, you bought Google ads against it, you iterated outward. That was not just a philosophy, it was a budget.

AI makes it much easier to spin up many different capabilities and potentialities at once. That lowers the cost of initial scope, which is the exact constraint the lean method was designed around.

The niche-and-iterate strategy is now, in his framing, much more competitive and much more aggressively tilled. If everyone is running the same incremental search over the same obvious adjacencies, the search space gets exhausted fast. His prescription is to de-correlate more aggressively from what everyone else is doing.

His evidence is a list of counterexamples: many of the most successful companies of the last ten years are, in his words, very anti-lean-startup. He names the frontier labs and Anduril. These are companies that started with a large, expensive, unhedged bet rather than a minimum viable slice.

What he does not say, and it matters: he does not say launch late. Stripe's own story is the counterweight inside his own answer. Ambitious scope, delayed public launch, live production user at month two. The synthesis he is actually describing is scope up, feedback loop unchanged.

The honest weakness of the argument is selection. Frontier labs and Anduril are survivors of a category whose failures are invisible and expensive. Anti-lean bets that did not work do not get invited to Startup School. He does not address the base rate.

## Schlep blindness, and the question he thinks founders skip

Harj raises schlep blindness, Paul Graham's term, and asks the pointed version: setting up payroll and learning financial services arcana is not why anyone starts a company. Is running a big company intellectually satisfying, sixteen years in?

Collison reframes rather than answers directly, and this is where the talk gets its published title.

He says the question founders skip is not "is this a good idea." It is "what if you succeed?" Before you raise significant capital, ask whether you will actually enjoy the thing you are signing up for. Are you going to want to work on this for ten years? Seventeen? Thirty?

The framing is useful because it inverts the usual failure analysis. Most advice optimizes for the probability of success. This optimizes for the conditional: given that it works, do you want the life on the other side.

His own answer for Stripe: every business is an applied theory of how some part of the world works, and Stripe gets to watch thousands of those theories get tested, from incorporation through to Shopify-scale and OpenAI-scale outcomes, staying in contact the whole way. His line: he has never met a Stripe customer and thought that was boring.

The supporting number he cites: roughly 25% of new Delaware corporations are started through Stripe Atlas. His figure, not independently verified here.

## Will the big labs eat every startup idea

Harj asks the fear directly.

Collison says the track record of large capable organizations crushing everything adjacent is checkered. His structural argument is about organizational capacity rather than capability: large organizations, however strong, are bad at aggressively pursuing a hundred priorities at once. Google looked omnipotent twenty years ago and still did not take everything it plausibly could have.

He adds a specific observation about labs. They tend to expand scope ambitiously, and ambitious scope expansion opens gaps rather than closing them. A company chasing everything is a company defending nothing in particular.

He also concedes the other side: the frontier labs have done extremely well and he expects that to continue. His claim is about the residual, not about who wins the middle.

## What the Stripe data says about right now

This is the numbers section, and it is worth citing carefully because all of it is Collison characterizing internal Stripe data from stage.

- New business formation on Stripe is up sharply year over year. One source records his characterization as around 2x; the more careful transcript notes say the relative change is the largest Stripe has recorded, larger than the 2019 to 2020 jump. Treat "2x" as the softer of the two claims.
- The median new business this year is performing better than the median new business a year ago. His point is that this is not only a volume story. The middle of the distribution moved.
- The probability that a new business reaches a given revenue threshold has improved. Thresholds named: $1M, $5M, $10M.
- Time to revenue has come down across those thresholds.
- His summary: by the objective metrics Stripe can see, there has never been a better time to start a business.

The driver he names is on the demand side, not the supply side. Enterprises are far more willing to buy from startups than they used to be. His explanation: the perceived risk of the status quo is now extremely high. A CIO who waits looks more exposed than a CIO who buys something unproven. Companies are adopting startup products at meaningful scale immediately, which compresses sales cycles that used to be the main reason enterprise-facing startups died.

He describes this as terror of being left behind, and says it has never been a better time for startups to sell.

## Centralization, and why he changed his mind

He came into the AI era worried about the opposite of what he now believes. The fear was that AI would be hegemonic and totalizing, with a handful of labs capturing most of the economic value.

What changed his mind was traffic. Not an argument, the volume and intensity of new companies starting and existing companies retooling, as seen from inside Stripe. He now expects many thousands of winners and a more decentralized world with broader-based prosperity.

He hedges immediately: the future is not predetermined and he tries not to operate on predictions.

## On predictions

He declines to forecast twice. The line he uses, on humanity's recurring conviction that a new technology means either permanent transformation or the end of everything: aviation was a genuinely big deal and it did not rewrite society the way people said it would. Then, roughly, that it is hard to predict anything, especially the future.

Read against the rest of the talk, this is the load-bearing caveat. The decentralization thesis and the "best time ever" data are both observations about the present that he explicitly refuses to extend forward.

He closes by saying Stripe would not exist without YC.

## What is genuinely actionable

Four things survive translation into something you can do on Monday.

Get a live production user inside two months, whatever your launch timeline. This is the transferable part of the Stripe story and the only part with a date attached. A long build is defensible. A long build with no user doing a real transaction is not.

Ask the success-conditional question before you raise. Not "will this work" but "if this works, do I want to be doing it in year ten." He is explicit that this is the question people skip, and it is cheap to ask.

Check whether your niche is already tilled. His claim is that incremental niche-and-iterate is now crowded, so the honest test is whether the adjacency you picked is one that a hundred other teams with the same tools would also pick. If yes, that is a signal to de-correlate, not a signal to move faster.

Sell into enterprises now if you were waiting. The specific claim is that the status-quo risk has flipped and buyers will take unproven products at scale. That is testable this quarter with a handful of outbound conversations, and it is falsifiable fast if he is wrong.

## Where he is talking his own book, and what is unverifiable

The data is all internal Stripe data, characterized verbally, unaudited, and from a machine transcript. Every number in the "best time ever" section is Stripe's own. Stripe benefits commercially and reputationally from the claim that business formation is booming, and Stripe Atlas is a direct beneficiary of more people incorporating. The 25% of Delaware corporations figure is his and is not independently verified here.

The population is also selected. Businesses that start on Stripe are online, developer-adjacent, and skew toward exactly the software categories AI is currently inflating. "Median new business on Stripe" is not "median new business." A 2x jump in Stripe signups is consistent with Stripe taking share, with AI making it trivial to spin up a company that later fails, and with genuine broad-based formation growth. He does not separate these.

The decentralization thesis is a directional inference from traffic he can see, offered by someone whose company's value scales with the number of businesses that exist rather than with the number of labs. He is candid that he came in believing the opposite, which is worth something, but the update runs toward his interests.

The anti-lean argument rests on survivors. Frontier labs and Anduril are two data points from a category whose failures are unusually expensive and unusually invisible. No base rate is offered.

The claim that dropping out costs nothing is drawn from a sample of one person who dropped out of MIT, had already sold a company, and had YC's network behind him. The reputational risk is plausibly near zero for that person and is not obviously zero in general.

His statement that he does not use models for writing is unverifiable and is the kind of thing that reads as principled regardless of whether it is current practice.

Two factual details did not survive verification: the location of Startup School 2009 (Berkeley in most sources, Burbank in one set of notes), and whether the new-business figure he cited was specifically 2x or a more general "largest jump on record."
