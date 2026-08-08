---
name: iteration-cost-method
description: Method for building hard, tightly coupled things with a small team by driving down the cost of a single iteration in software and in the physical world. Use when a project's real constraint is cycle time rather than headcount; when deciding what to build in-house versus buy; when a team argues from spreadsheets instead of from a simulator; when picking a demonstrator or wedge product; when a regulation blocks a product and you are choosing between confrontation and engagement; or when someone claims a task needs a large team. Derived from Blake Scholl's YC Startup School 2026 talk.
---

# Iteration cost method

Source: Blake Scholl (founder, Boom Supersonic), YC Startup School 2026, "The Future Was Supposed to Be Faster." Video: https://www.youtube.com/watch?v=byAj35QlGbs

Context: a 50-person team built XB-1, a supersonic demonstrator that reached Mach 1.1, and the flight data was used to get civil supersonic flight legalized over the US. The method below is how that headcount was possible. It generalizes past aerospace.

## The one-line version

Find the number that sets your cycle time, own that thing, and spend your engineering budget on making one iteration cheap rather than on making each iteration right.

## 1. Measure the cost of one iteration, in bits and in atoms

Two numbers, tracked separately.

Bits: how long from wanting to evaluate a design change to having an answer.
Atoms: how long from a finished design to a physical thing you can test.

Most teams try to improve their hit rate per cycle. Improving cycle count usually beats it, because a faster loop finds problems that no amount of upfront care predicts. Before optimizing anything else, write down both numbers for your project. If you cannot state them, that is the first finding.

Large organizations lose on this axis and know it. The pace reference Scholl uses is two or more years to build a single missile interceptor. At that cadence a program gets a handful of learning cycles per decade, and no amount of talent compensates.

## 2. Turn spreadsheet engineering into real software

The pattern to look for: specialists each holding an analysis in their own spreadsheet, handing results to each other in sequence. It is the slowest arrangement possible for anything where changes propagate across disciplines.

Replace it with a simulator. At Boom this was MakeBoom: an aircraft is defined in a configuration file, a script runs a whole-aircraft simulation, and results come back in minutes covering range, fuel burn, capacity, and the trades between them.

Once the analysis is code, apply the practices that only work on code: version control, automated testing, continuous integration on design changes. A design change gets validated like a commit.

The narrower version, for a specific bottleneck: a tool that gives real-time feedback on one high-iteration component. Boom's blade design tool put structural and aerodynamic consequences in front of an engineer live, compressing what would have been dozens of engineers over months into a couple of engineers iterating.

Why this is now affordable: AI dropped the cost of writing software enough that custom internal engineering tools are within reach of a startup. They used to require Amazon-scale justification. The person who needs the tool can now build it.

## 3. Do not chase modularity in things that cannot be modular

Software gets its speed from interfaces that let you change one part without touching others. Some artifacts have no such interfaces. In an aircraft, adding a row of seats makes the fuselage heavier, which demands more thrust, which changes the wing.

If the artifact cannot be decoupled, do not fake it with abstractions. Simulate the whole thing at once, fast. Whole-system simulation in minutes is the substitute for modularity, not a supplement to it.

Apply the test directly: is my system genuinely decoupled, or am I maintaining interface ceremony over something where every change propagates anyway? If the latter, invest in whole-system evaluation instead of in boundaries.

## 4. Vertically integrate what sets your cycle time, and nothing else

This is a speed decision, not a cost or margin decision. The test is whether an outside dependency controls how fast you learn.

What Boom brought in-house and why:

- An R&D machine shop, taking a digitally designed engine part to a prototype part in about 24 hours, with engineers and machinists working side by side instead of across a purchase order.
- Their own engine test stand, roughly 30 minutes from engineering, so testing does not require booking someone else's cell.
- Their own factory, for the same reason at production scale.

The stated reason for all of it: outside suppliers in this industry are very difficult to iterate with, on lead time and on working culture.

Keep outsourcing everything that does not gate the loop. In-housing is expensive and only pays where it converts waiting into iterating.

## 5. Search the design space before committing to one design

The most underused function of a fast simulator is choosing what to build, not validating what you already chose. Boom used theirs to survey the space of conceivable supersonic aircraft looking for product-market fit before committing to metal.

Most teams skip this because the decision was made before the tool existed. When you build the simulator, re-open the decision. Run the trade study you would have run if you had the tool first.

## 6. Pick the demonstrator that resolves your largest unknown

XB-1 existed because they did not know what building a supersonic passenger aircraft would take. It was a learning instrument, never a product, and never carried a paying passenger.

Choose the smallest artifact that forces the unknowns into the open. This is often not the smallest shippable product, and confusing the two produces demos that prove nothing you were unsure about.

Second-order returns to build for: it generated the data that changed the regulation, and it created a precedent nobody else held.

## 7. When a regulation blocks you, check whether it measures the right variable

The supersonic overland ban regulated speed. The actual harm was the sonic boom reaching the ground. XB-1 demonstrated Mach cutoff: at high enough altitude and within a window of speed and atmospheric conditions, the shock refracts upward and never reaches the surface. Supersonic, and quiet on the ground.

That reframing beats asking for an exemption, because it gives the regulator a defensible basis to act on rather than a favor to grant.

On posture, engage early when three conditions hold: the domain is safety critical, credibility once lost is unrecoverable, and no incumbent is lobbying to keep the rule. Boom went to the FAA before plans were final and asked for feedback rather than permission, framed as both parties against the problem. The permit came in about 90 minutes because the work was already done. The Uber approach of ignoring regulators worked in a domain with none of those three conditions.

Timeline, for calibration on how fast this can move once evidence exists: sound barrier broken, West Wing invitation within 24 hours, executive order 115 days later, then unanimous House passage and unanimous Senate Commerce Committee approval.

## 8. Fund the long program with a near-term product built from the same core

Boom adapted its engine core into a natural gas ground power turbine, sold as a separate product with first customer delivery expected within a year.

Three returns from one investment: revenue from a market buying today, reliability and test data accumulated on paying customers rather than on your own test budget, and a business that survives if the long program slips.

Look for the adjacent market that will buy your core technology before your actual product exists. This is stronger than milestone-based fundraising because it converts your R&D into an asset that produces evidence and cash at the same time.

## 9. Compete on the next process, not the current one

Trying to win at a manufacturing process someone else already optimized means competing on their axis. Boom's counter-move was an all-digital, tooling-free turbine blade process going from digital design to finished blade in 24 hours, versus conventional dies and fixtures with lead times in weeks or months.

The general form: when you cannot win on the current cost structure, find the process where the current cost structure does not apply.

Known limit, stated in the talk: physical-world AI is not there yet and CNC programming is still manual. The compression is in design, not in execution.

## Checklist

- [ ] Write down cycle time for bits and for atoms. Identify which one gates you.
- [ ] Find the spreadsheet that several people hand between each other. Turn it into code with tests.
- [ ] Ask whether your system is truly decoupled. If not, build whole-system evaluation instead of interfaces.
- [ ] List every outside dependency that controls your cycle time. In-house those and only those.
- [ ] Re-run the build decision with the simulator you now have.
- [ ] Name your largest unknown and the smallest artifact that resolves it.
- [ ] For each blocking regulation, ask what it measures and whether that is the actual harm.
- [ ] Find the adjacent market that will pay for your core before your product exists.

## What this method does not cover

The 50-person figure applies to a single-seat demonstrator. Certifying a passenger airliner is dominated by documentation, testing, and regulatory process, and none of that compresses the way design analysis does. Do not carry the headcount claim into a domain where the work is compliance rather than iteration.

The talk contains no dollar figures, so the efficiency claim cannot be checked against a budget. Treat the method as a description of where the leverage sits, not as evidence about how much it saved.
