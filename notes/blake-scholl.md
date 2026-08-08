# The future was supposed to be faster
### Notes on Blake Scholl's YC Startup School 2026 talk

Source: Blake Scholl (founder, Boom Supersonic, YC W16), YC Startup School 2026.
Video: https://www.youtube.com/watch?v=byAj35QlGbs
Transcript: https://www.ycrootaccess.com/p/blake-scholl-the-future-was-supposed

The talk is published under the title "The Future Was Supposed to Be Faster." The
"How 50 People Built a Supersonic Jet" framing is a section of it, and it is the part
worth studying, because the rest is motivational.

---

## The claim being made

A team of 50 people built a supersonic jet that flew faster than sound. Scholl's
framing is that this used to require thousands of people and billions of dollars, and
that the gap is now closable by a startup. Everything interesting in the talk is the
mechanism behind that claim, so most of these notes are about mechanism rather than
about the mission.

Read the claim carefully before accepting it. XB-1 is a one-seat demonstrator, not an
airliner. The 50-person figure attaches to XB-1 specifically. Scholl is explicit that
Overture, the passenger aircraft, still needs billions in R&D capital. The talk does
not claim 50 people can certify an airliner, and neither should anyone repeating it.

---

## Why the future stopped getting faster

The opening argument is a stagnation argument with a specific date attached. 1969 gave
us the moon landing and Concorde. Since then, commercial aviation has gotten cheaper,
safer, and more fuel efficient, but not faster. Scholl's comparison is that the 787 is
an aesthetic refresh of the 707 layout rather than a step change in what flying does
for you.

The counterexample he leans on is the first jet airliners, which roughly doubled cruise
speed over what came before. He attributes second-order consequences to that: Hawaii as
a mass tourist destination, manufacturing relationships spanning the Pacific, touring
musicians reaching a global audience. The point is that speed is not a luxury feature.
It changes which places count as reachable, and reachability changes economies.

The line that lands is a throwaway: there has been more progress in supersonic music
than in supersonic flight since Concorde.

---

## Why no incumbent did it

Scholl gives four reasons, and they are worth separating because only some of them are
about technology.

Boeing stopped launching genuinely new airliners and optimized the 737 and 787 lines
instead. A clean-sheet supersonic program is a bet against that revenue, and no
incumbent wanted to own the regulatory risk either. Status quo was the profitable
position.

The obvious wedge product, a supersonic business jet, was dead on arrival in the US,
because supersonic flight over land was banned. Most business jet miles are overland.
Without regulatory change the economics never close, so nobody built the product, and
because nobody built the product nobody lobbied for the regulatory change.

Iteration cycles inside large aerospace and defense programs run in years. He cites two
or more years to build a single Patriot interceptor as the pace reference. At that
cadence you cannot learn your way to a new aircraft, because you get a handful of
learning cycles per decade.

Underneath all of it is a supply chain argument he returns to later: the US tool and
die base was hollowed out and largely moved to China, so anyone building physical
things in America is waiting in someone else's queue.

---

## Why build XB-1 at all

The honest answer he gives is ignorance. They did not know what building a supersonic
passenger aircraft would actually require, and concluded the only way to find out was
to build a supersonic jet first. XB-1 was a learning instrument.

It did three jobs beyond learning. It proved a private team could reach supersonic
flight. It produced the flight data behind the sonic boom argument. And it created the
regulatory precedent that everything after depended on.

Sequencing note worth stealing: the demonstrator was chosen because it was the smallest
artifact that would generate the specific unknowns they needed resolved, not because it
was a shippable product. It never carried a paying passenger and was never meant to.

---

## What XB-1 actually did

Concrete results claimed in the talk:

- First privately developed supersonic jet, and the first supersonic jet made in
  America outside a government or military program.
- Broke the sound barrier across six passes on two flights, reaching Mach 1.1. Public
  record puts the first supersonic flight in January 2025, roughly a year before the
  talk.
- Received the first permit ever issued for flying a civil supersonic airplane.
- First human-piloted airplane landed entirely on augmented reality, with no natural
  view of the runway. XB-1's nose geometry made a conventional forward view impractical,
  so the fix was a display rather than an airframe change.
- First supersonic air-to-air livestream, run over Starlink from an iPhone.

The last two are the tell for how this team works. Both are cases of solving a hardware
problem with software and consumer parts instead of with metal.

---

## Mach cutoff, which is the load-bearing technical result

The regulatory objection to supersonic flight is the boom on the ground, not the speed.
Scholl's argument is that these were conflated: the ban was written against speed when
the actual harm is ground noise.

XB-1 demonstrated Mach cutoff. Above a certain altitude, and within a window of speed
and atmospheric conditions, the shock wave refracts in the temperature gradient and
turns back upward before it reaches the surface. His description is that the boom makes
a U-turn in the sky and never touches the ground. The aircraft is supersonic and the
ground is quiet.

This is real physics and not new physics. What was new was flight data from a civil
aircraft demonstrating it, which is the thing a regulator can act on. Note the shape of
the move: they did not lobby to relax a noise limit, they produced evidence that the
rule was measuring the wrong variable.

---

## The regulatory arc

This is the most transferable part of the talk for anyone in a regulated market, and
Scholl is careful to say the strategy is context dependent.

Boom went to the FAA early, before plans were final, and asked for feedback rather than
permission. His framing of the goal: Boom and the FAA against the problem, rather than
Boom against the FAA. When XB-1 was ready, the permit came through in about 90 minutes,
because the work had been done in advance.

The sequence after the supersonic flight moved fast:

- Within 24 hours, an invitation to the West Wing.
- 115 days after breaking the sound barrier, an executive order legalizing civil
  supersonic flight over the US.
- Legislation to make it durable passed the House unanimously.
- The week before the transcript was published in late July 2026, the Senate Commerce
  Committee approved it unanimously.

He contrasts this deliberately with Uber, which grew by ignoring regulators. His
reasoning for why that was wrong here: aviation is safety critical, so an adversarial
posture forfeits credibility you cannot rebuild, and unlike the taxi industry there was
no entrenched incumbent lobbying against him. Nobody was defending the boom ban. That
asymmetry is what made engagement cheaper than confrontation.

---

## How 50 people did it, part one: iteration in bits

Scholl's organizing idea is the cost of a single iteration, split into bits and atoms.
Everything they built is aimed at driving one of those two numbers down.

On the bits side, the problem was that aircraft engineering historically lives in
spreadsheets owned by individual specialists who hand results to each other in
sequence. Aircraft design is tightly coupled, so every change propagates. Add a row of
seats and the fuselage gets heavier, which demands more thrust, which changes the wing.
Sequential handoffs across coupled disciplines is the slowest possible arrangement.

Their answer was MakeBoom, an internal tool where an aircraft is defined in a
configuration file and a script runs a whole-aircraft simulation in minutes, returning
range, fuel burn, capacity, and the trades between them. His description of what it
changed: instead of arguing about which airplane to build, they could search the space
of conceivable supersonic jets and look for product-market fit before committing to
metal.

The second tool is Blade Runner, for turbine blade design. An engineer changes a blade
and sees structural and aerodynamic consequences in real time. He claims this compresses
work that would have taken dozens of engineers many months into a couple of engineers
iterating live.

That is where the headcount number actually comes from. It is not that 50 people did
the work of thousands by working harder. It is that a large share of the historical
thousands were doing analysis that is now a script, and the remaining people are the
ones deciding what to analyze.

---

## What transfers from software to hardware, and what does not

Scholl is more careful here than the usual "treat hardware like software" pitch, and
the distinction is the useful part.

What transfers is the engineering process. Spreadsheet engineering is described as baby
software, and once it is real code you can apply version control, automated testing,
and continuous integration to design analysis. A design change gets validated the way a
commit does.

What does not transfer is modularity. He rejects it outright for aircraft. Software
gets its speed from clean interfaces that let you change one module without touching
others. An airplane has no such interfaces, because mass, drag, and thrust couple
everything to everything. His conclusion is that if you cannot decouple the artifact,
you have to be able to simulate the whole thing at once, quickly. Whole-aircraft
simulation in minutes is the substitute for modularity, not an accompaniment to it.

---

## How 50 people did it, part two: iteration in atoms

Simulation only helps until you need a physical part. Their constraint was that
external aerospace suppliers are, in his words, very difficult to iterate with, both on
lead time and on culture.

So they brought the loop in-house, and each decision has a stated reason that is about
speed rather than cost:

- An R&D machine shop in Denver, so a digitally designed engine part becomes a
  prototype part in about 24 hours, with engineers and machinists working side by side
  rather than across a purchase order.
- Their own engine test stand, about 30 minutes from engineering, so they can test
  whenever they want instead of reserving time in someone else's cell.
- Their own factory, under construction as of January 2026, first machines installed by
  June, with first production engine parts expected within weeks of the July 2026 talk.

The general principle: vertically integrate the thing you need to iterate on. Not
everything, and not for margin. The test is whether an outside dependency sets your
cycle time.

---

## Tooling-free manufacturing and the China argument

The sharpest specific claim in the talk. Conventional turbine blade manufacturing needs
custom precision tooling, meaning dies, molds, and fixtures, with lead times in weeks or
months, made worse by the shortage of US tool and die capacity. Boom claims an
all-digital process that goes from digital design to a finished turbine blade in 24
hours with no tooling at all.

He generalizes this into a manufacturing policy view. Trying to repatriate the old
labor-intensive, tooling-heavy processes means competing with China on the axis China
already won. The alternative he proposes is to invent the next process, where tooling
does not exist and the cost structure is set by digital iteration speed rather than
labor.

He also marks the limit honestly. Physical-world AI is not there yet, and programming a
CNC machine remains a manual job. The automation is in design, not in execution.

---

## Funding a hard thing without betting the company on it

The structural move that deserves the most attention. Boom adapted its engine core into
Superpower, a natural gas turbine for ground-based power generation, with first customer
delivery expected within 12 months of the talk.

Three things come out of the same investment. Revenue from a market that is buying now.
Reliability and test data on the core, accumulated by paying customers rather than by
Boom's own test budget. And a business that survives if the airliner schedule slips.

This is a considerably better answer to "how do you fund a decade-long hardware program"
than raising against milestones. Whether it works depends on how much of the core is
genuinely common between a ground turbine and a certified aviation engine, which is
exactly the thing an outsider cannot check.

---

## Hiring and what he looks for

He wants early-career engineers and says so bluntly, on the theory that people who have
not yet learned how aerospace has always been done are cheaper to redirect. His claim
that experience wins in hardware is a myth told by old people at big companies is
self-serving, and he does not pretend otherwise.

The parts that survive that discount: the trait he ranks first is caring, since skills
are teachable and motivation is not. He wants hands-on builders with side projects,
people who have finished something physical without being assigned it. One rule has
real content, which is that if someone has done the thing before, call them, not to be
bound by the answer but to know what is already known. He promotes from within to hold
culture, and warns against becoming an expert too quickly, on the grounds that
expertise encodes the state of the field at the moment you acquired it.

He also moved the company from San Francisco to Denver to build physically at scale
affordably, while still telling students to move to an ambition-dense city. He does not
reconcile those two.

---

## What transfers to software startups

Strip the aerospace and this is what is left.

Measure your iteration cycle time and treat it as the primary metric. Most process
improvements are attempts to be right more often per cycle. Getting more cycles usually
beats that.

Build the internal tool. His argument that AI made custom engineering tools affordable
at startup scale is the version of "build vs buy" that has actually changed recently.
The tool that encodes your specific trade space was previously an Amazon-scale luxury.
If your team argues from spreadsheets, that is a tool waiting to be written.

Vertically integrate exactly the dependency that sets your cycle time, and outsource the
rest. The machine shop was not about margin. It was about not waiting.

Search the design space before committing. MakeBoom's real function was choosing which
aircraft to build rather than validating one already chosen. The software analogue is
cheap simulation of product decisions before the engineering commitment, which most
teams skip because they have already decided.

If you are in a regulated market, find out whether the rule is measuring the right
variable. The boom ban regulated speed when the harm was ground noise. Producing data
that reframes the measurement is a different and often better move than asking for an
exemption.

Pick the demonstrator that resolves your largest unknown, not the smallest shippable
product. These are sometimes the same thing and often not.

---

## Where he is talking his own book

Worth flagging, because the talk is a recruiting and fundraising artifact as much as it
is a lecture.

The 50-person figure covers XB-1, a single-seat demonstrator. Certifying a passenger
airliner is a different problem dominated by documentation, testing, and regulatory
process, none of which compresses the way analysis does. The talk lets the 50 number sit
next to the Overture ambition without separating them.

No dollar figures appear anywhere in the transcript. There is no XB-1 program cost, no
total raised, no Overture development budget, and no ticket price. "Cheaper than
government programs" is not a number, and the efficiency claim cannot be checked without
one.

Overture specifics are absent too. No passenger count, no range, no cruise speed, no
order book, no first flight date, and the airliner engine is not named. For a company
whose case rests on that aircraft, this is a lot of missing detail.

Current Boom headcount is never stated. The company is certainly much larger than 50
now, and the talk never says by how much.

Mach cutoff works within a window of altitude, speed, and atmospheric conditions.
Whether that window is wide enough for scheduled airline service across real routes,
seasons, and weather is the entire commercial question, and the talk asserts the physics
without characterizing the window.

The 24-hour tooling-free turbine blade is stated without any qualification about which
blade, what material, what tolerance, or whether the parts have accumulated
certification-relevant hours. It is the most impressive claim in the talk and the least
verifiable.

The regulatory story is told as a strategy success. Some of it is a timing success. An
administration receptive to deregulation arrived at a useful moment, and the absence of
an opposing lobby did more work than the engagement approach did. His own framing
concedes the second point.

Superpower's dual-use logic depends on real commonality between a ground turbine and a
certified aviation engine. From outside there is no way to tell how much of the core is
actually shared versus how much is a related product sharing a name.

Finally, survivorship. This is a founder describing the decisions of a company that is
still alive and shipping, roughly twelve years in, having gone supersonic once with a
demonstrator. The same decisions with worse luck produce a company nobody invites to
speak.
