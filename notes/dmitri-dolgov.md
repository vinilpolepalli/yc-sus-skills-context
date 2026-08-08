# Dmitri Dolgov: the demo is only 1% of the work

Speaker: Dmitri Dolgov, Co-CEO of Waymo. Event: YC Startup School 2026.
Talk title: "The Demo Is Only 1% Of The Work."
Video: https://www.youtube.com/watch?v=Gp4zrV3-6N8
Transcript source: https://www.ycrootaccess.com/p/dmitri-dolgov-seven-lessons-from

The talk is organized as seven lessons drawn from seventeen years of building the
Waymo Driver. The through-line is that the difficulty of physical-world AI is not
the first working version. It is everything between the first working version and
a product people trust with their bodies.

## The framing number

The title is the argument. Waymo got to something demo-worthy in roughly eighteen
months. The product took fifteen years. Dolgov's point is not that Waymo was slow.
It is that the ratio between those two numbers is a property of physical-world
autonomy, and founders routinely mistake the first number for the whole job.

His compressed advice to the room: count your nines before you count your demo
views.

## Lesson 1: the gap between a demo and a real product

The origin story sets the scale. The project started in 2009 with about a dozen
engineers and two explicit goals: drive 100,000 autonomous miles, and complete ten
routes of 100 miles each, chosen to span varied Bay Area conditions, with no human
intervention. Both were done in about eighteen months. Dolgov stresses this
happened before the modern stack existed, before ConvNets and before Transformers.

So a small team hit roughly 90% capability with pre-deep-learning methods in a year
and a half. Then the remaining work took thirteen more years.

The model he uses is the ladder of nines. Reliability is exponential, not linear.
Each additional nine of reliability costs roughly ten times the effort of the one
before it. A demo needs one nine. A copilot or assist product, where a human stays
in the loop and absorbs failures, needs a few nines. A fully autonomous agent that
removes the human needs the whole stack of nines.

The consequence founders miss: the methods that buy you the early nines do not buy
you the later ones. The first couple come from ordinary engineering and bug fixing.
The next ones require different architecture entirely, redundant systems and tiered
fallbacks. You cannot reach them by doing the same thing for longer. This is the
most useful claim in the talk and the one most often stated vaguely elsewhere.

Related failure mode he names: spending on the demo what you should be saving for
the nines. Hype cycles reliably produce spectacular demos and very few products.

The long tail statement is worth keeping verbatim in spirit: at sufficient scale, a
once-in-a-million-miles event becomes a daily occurrence. Rarity is a function of
your deployment volume, not a property of the event.

## The exponential on the other side

The counterpoint, and the reason the fifteen years is presented as an investment
rather than a cautionary tale: it took fifteen years to reach the first 100 million
fully autonomous miles, and about seven months to drive the next 100 million.

Current operating numbers he cites:

- 500,000 trips per week
- more than 4 million fully autonomous miles per week
- 15 US cities
- more than 20 million fully autonomous trips to date
- more than 200 million fully autonomous miles to date

Scaling cadence: eight years to reach four cities, then four new cities launched in
a single day in 2026.

## Lesson 2: pick the right technology curve

The failure he describes is choosing the technology with the fastest early ramp,
riding the steep part, and then discovering the curve flattens below the
performance your product actually requires. By the time you find the plateau you
have built an organization and a codebase around the wrong slope.

His applied example is sensing, and it is the closest the talk comes to a
competitive jab, though he never names anyone. Humans drive with eyes alone, so
camera-only is an existence proof that vision can drive a car. But the target for a
driverless product is not human parity. It is strongly superhuman safety. Weak
sensing produces a safety curve that flattens too early to get there. Camera-only
is fine for an assist product where a human covers the tail.

Waymo runs cameras, lidar, and radar, and he insists these are not backups for one
another. Cameras give resolution and color but are passive and degrade in darkness
and glare. Lidar measures 3D structure directly and works in total darkness. Radar
penetrates fog, rain, and snow and reads Doppler velocity directly. Fused, they
produce a view he claims is better than any single modality can reach.

The supporting footage he shows: a Phoenix dust storm where the camera is largely
blind and lidar still resolves a pedestrian at the roadside; a night scene where
pedestrians are about to climb a concrete barrier and lidar sees the motion the
camera cannot; children chasing a dog with no ambient light. He also tells a small
operational story about a branch landing on a sensor that the wipers could not
clear, where redundancy let the vehicle drive itself back to the depot rather than
stop in traffic.

Hardware note aimed at founders: do not anchor your plans to today's component
prices. Costs fall across generations. Betting the company on a current bill of
materials is betting on a number with a short shelf life. Waymo is on its sixth
generation of hardware, across Jaguar I-PACE, Hyundai Ioniq, and Zeekr platforms.

## Lesson 3: ride every technology wave

Waymo rebuilt the Driver around each successive wave: convolutional networks for
perception around 2013, Transformers across perception, behavior prediction, and
planning around 2017, and now VLMs and frontier world models.

The hard part, he says, is not the research. It is carrying bleeding-edge research
into production in a safety-critical system without regressions, while the product
keeps scaling underneath you.

His launch criterion for adopting a new wave is the part worth stealing. Do not
only ask what the new technology gives you. Also ask two questions:

1. Has it simplified my stack?
2. Has it led to fragmentation or unification?

The failure mode he names is the successful tiger team that produces a genuinely
better result with no integration path, which becomes a dead end and leaves the
organization carrying two systems. He treats radical simplification and
unification as a requirement for shipping a new approach, alongside the performance
gain. Performance alone is not sufficient justification.

He also observes that driving resembles language modeling more than it first
appears: a continuous negotiation with other dynamic actors conducted in body
language rather than words.

## Lesson 4: the bitter lesson still wins, with a qualifier

He restates Sutton's bitter lesson plainly. General methods that leverage large
compute and large data beat methods built on handcrafted human knowledge.

Then the qualifier, which is the actual content: structure that fights scale always
loses, and structure that channels scale always wins. His illustration is a
Go-playing robot, where hand-coding Go strategy fights scale but giving the system
a representation of the board channels it.

Waymo's version is what he calls structure-augmented end-to-end. Rather than a pure
black-box model, they materialize intermediate structured representations of
semantic and physical state alongside the learned embeddings. He claims three
benefits:

- a real-time safety validation layer at inference, checking a legible
  representation rather than trusting the end-to-end output blindly
- training and evaluation efficiency, since you can mix full end-to-end training
  with training against the compact intermediate representation
- verifiable feedback signals usable for reinforcement learning and loss design

The Waymo Foundation Model itself he describes as a multimodal world action
language model: a multimodal encoder over camera, lidar, and radar; a dual-pathway
decoder with a fast reflex path handling millisecond geometric and safety reactions
and a slow path doing semantic reasoning; and a generative component that predicts
what other actors will do and supports planning. He explicitly maps this to
system one and system two.

## Lesson 5: every physical AI company needs a simulator

His strongest claim here is that a simulator is not tooling. It is a large AI model
in its own right, and should be resourced accordingly.

Two kinds are needed, and they arrived in different eras. Behavioral world models
came first, covering physics, semantics, traffic, and weather. Sensing world models
became necessary once the driving stack went end-to-end, because a system that
consumes raw sensor data cannot be evaluated against a simulator that only produces
abstract object lists. The simulator has to be realistic at the sensor level.

Waymo's world model builds on Google DeepMind's Genie 3 for controllable and
realistic scenario generation across both behavior and sensing.

The payoff is generating rare events they have never encountered on the road:
stranded vehicles on freeways, a plane landing on a freeway, an elephant in an
intersection, snow on the Golden Gate Bridge, a dinosaur in traffic. The
deliberately absurd examples make a real point, which is that the long tail cannot
be waited for at the rate the product needs it.

Notable omission: he never gives a simulated-to-real mileage ratio, which is the
number an outsider would want in order to judge how much of the safety case rests
on simulation.

## Lesson 6: build an AI flywheel

Three pillars, sharing generative capability from the same foundation model:

- the agent, meaning the Driver itself
- the simulator, the playground it learns in
- the critic, which scores performance rigorously

The loop: real deployment produces data, data grounds the simulator, the simulator
generates harder edge cases, the agent learns from them, the improved agent
redeploys.

The line that carries the lesson is the caveat, not the loop. A flywheel will spin
in any direction, or in place. Metrics are what point it somewhere. A team can run
a fast iteration loop for years and go nowhere if the scoring function is wrong or
absent.

## Lesson 7: evals are your competitive advantage

Ordering advice, stated twice: build your eval before you build your technology,
and build your eval and metrics before you build your product.

He distinguishes open-loop from closed-loop evaluation. Open-loop scores passive
input-output pairs, which is what imitation learning naturally gives you.
Closed-loop lets the action change the world, update the sensors, and feed the next
action. For any safety-critical agent he calls closed-loop essential, because the
compounding of your own mistakes is the thing you need to measure and open-loop
evaluation hides it by construction.

Second point: model-level evaluation is not enough. Waymo's safety and readiness
framework covers the physical layer, the onboard behavioral layer, offboard
components, and operational processes. The system that is deployed is not the
model.

Published safety numbers he cites, drawn from more than 220 million fully
autonomous miles:

- roughly 17 times fewer serious-injury crashes than human drivers
- equivalent to preventing a serious injury about every eight days
- context figure: a road fatality somewhere in the world every 26 seconds

The strategic argument for publishing: models leak and algorithms get replicated,
but hundreds of millions of autonomous miles backed by evidence-grade evaluation
and public audit are much harder to copy. In his framing the eval corpus, not the
model, is the moat.

His summary line on why: in the physical world, trust is everything, and evaluation
and metrics are how trust gets earned.

## The closing

He tells a small story about riding with his children while two drivers cut in
front of the vehicle, handled smoothly enough that the kids in the back never
looked up. His gloss: the best AI moments look like nothing happened. That is a
neat inversion of the demo incentive, since nothing-happened does not make a good
clip.

He closes by placing physical AI roughly where digital AI was a few years ago, and
predicting the next decade happens in the physical world.

## What is actually actionable at small scale

Most of the talk describes things only a capital-rich company can do. These parts
transfer regardless of size.

Count nines, not demos. Write down the reliability your product actually needs
before you build it, and be honest that a human-in-the-loop product and an
autonomous one are separated by orders of magnitude, not by polish. This costs
nothing and changes what you build.

Build the eval first. This is the cheapest item on the list and the one most
startups skip. It is also the one Waymo says compounds into a moat. You do not need
220 million miles to start; you need a scored set of the cases you keep failing.

Insist on closed-loop evaluation wherever your agent's output changes its own next
input. Any agentic product has this structure. Offline accuracy on a fixed dataset
will systematically flatter you.

Apply the two adoption questions to every new model or framework: does it simplify
the stack, and does it unify or fragment. A small team can be killed by carrying
two systems in a way a large one cannot.

Watch for the curve that flattens. Ask what the ceiling of your chosen approach is,
not its current slope. This is a thirty minute exercise that people avoid because
the answer can be unwelcome.

Guide the flywheel with a metric. If you cannot state the number your iteration
loop is supposed to move, you are iterating in place.

Do not anchor to current component prices, or in a software context, current token
prices and current model capability. Both move fast enough to invalidate a plan
built on them.

## Where he is talking his own book

This is a Waymo executive making the case for Waymo's technology choices, and
several lessons are shaped to fit choices Waymo already made.

The sensing argument is the clearest example. The claim that weak sensing flattens
too early is presented as a general law, but it is also a defense of an expensive
lidar-based stack against a cheaper camera-only competitor that has not yet reached
the plateau he predicts. The prediction may be correct. It is still a prediction
about a curve that has not finished, made by the party with the most to lose if it
is wrong. The dust storm and darkness clips are real demonstrations of lidar's
advantage in specific conditions; they do not establish that the camera-only safety
curve cannot get there by other means.

The fifteen-years-then-seven-months story is presented as vindication of patience.
It is equally consistent with an alternative reading in which most of those fifteen
years were spent waiting for deep learning, compute, and sensor cost curves that
arrived from outside Waymo. He notes himself that the 2010 demo predated ConvNets
and Transformers. A founder taking "be patient for fifteen years" as the lesson may
be drawing the wrong conclusion from a company that survived because its parent
could fund it through that period. Almost no startup has that option, and he does
not address the funding question at all.

The safety statistics come from Waymo's own published analysis. The comparison is
against human drivers over 220 million miles, but those miles are concentrated in
mapped, geofenced, mostly warm-weather cities that Waymo selected. The human
baseline is drawn from broader driving conditions. Waymo does publish its
methodology and third parties have engaged with it, which is more than most, but
17x is not a like-for-like comparison and the talk does not flag the caveat.

Unverifiable from outside: the claimed benefits of structure-augmented end-to-end
over vanilla end-to-end, the assertion that the simulator is good enough to train
and evaluate with high confidence, and the entire foundation model architecture
description. None of it is falsifiable by an outside observer, and no ablation
numbers are given.

The moat argument is self-serving in an interesting way. Framing accumulated
evaluation data as the durable advantage is convenient for the incumbent with the
most miles, and it happens to justify openness about safety data as strategy rather
than obligation. It may still be true.

Missing entirely: unit economics, cost per mile, whether the business is profitable,
depot and fleet operations at scale, remote assistance, and how much human
intervention sits behind the autonomous miles. For a talk about the 99% of work
after the demo, the operational and financial 99% goes unmentioned.
