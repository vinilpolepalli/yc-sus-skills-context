# The mindset that built NVIDIA
### Notes on Jensen Huang's YC Startup School 2026 conversation with Garry Tan

Source: Jensen Huang (NVIDIA), interviewed by Garry Tan, YC Startup School 2026, Chase Center.
Video: https://www.youtube.com/watch?v=I4B37S1dyQQ
Transcript used for these notes: https://www.ycrootaccess.com/p/jensen-huang-the-mindset-that-built

Working notes. Everything is paraphrase unless it sits inside quotation marks. Figures are
Jensen's own as stated, not independently verified; the last section flags the shaky ones.

---

## The hook: the company was founded on the wrong algorithm

Garry opens by asking what the early story is that students should understand. Jensen does
not reach for a triumph. He goes straight to the failure:

> "The choice of our technology that we started the company with was absolutely wrong."

The setup. NVIDIA started in 1993 with a bet about the PC: a personal computer could be turned
into a game console if you built it a 3D graphics accelerator. The technical claim underneath
was that rendering which then required a large workstation or supercomputer could be
re-derived and compressed into a chip cheap enough for a consumer PC. In his framing, they set
out to "reinvent the algorithm that would require these large supercomputers and fit it into
the PC."

So they invented a new algorithm. They were excited about it. And in his words, "it turns
out the algorithm was exactly wrong."

## What exactly was wrong, and what he does not say

This is the part worth pinning down carefully, because it is easy to fill in from outside
knowledge and get the talk wrong.

What he actually says in this conversation:

- The mistake was at the level of the core rendering algorithm the company was founded on,
  not a bug, not a schedule slip, not a market timing error. The technical foundation was
  the wrong one.
- They discovered it in 1995, roughly two years in.
- By the time they discovered it, "there were some 35, 40 other companies that were building
  3D graphics for PCs." So they were late, wrong, and crowded simultaneously.
- The compounding problem was not just that their approach was wrong. It was that
  "none of us knew how to do it the right way." The company had no internal expertise in the
  approach the industry was converging on.
- The correct approach was the OpenGL model of a graphics pipeline. That is the thing they
  had to learn from zero.

What he does not say, and what these notes will therefore not assert: he never names the
product, never says NV1 or RIVA 128, never uses the words quadrilateral, triangle, or texture
mapping, and never mentions Microsoft or Direct3D. The widely told version outside the talk
is that NVIDIA's first chip rendered curved surfaces from quadrilateral primitives while the
industry standardized on triangles, leaving the chip incompatible with the software everyone
was about to write. That is consistent with what he describes, but he does not say it here.
Cite the talk for the shape of the story and a hardware history for the specifics, not both
at once.

## The fix: three textbooks

The recovery mechanism is deliberately unglamorous, and that is the point of telling it.

Jensen went to Fry's Electronics with, as he puts it, a couple of sixty dollar books and a
couple of hundred dollars in his pocket, and bought three textbooks on OpenGL and how to
design OpenGL pipelines. He handed them to his engineers. That was the retraining program.

His summary of the outcome is characteristically immodest: "We reinvented computer graphics.
We're the world leader in modern computer graphics."

The lesson he draws is not about graphics. It is that the specific technology a company is
built on is not the durable thing:

> "Technology's changing all the time. So long as you're able to confront reality, so long
> as you are able to learn, the technology itself actually doesn't matter."

And the framing of the decision itself, which is the actual transferable move:

> "We won't have a company if we don't confront the fact that this doesn't work and start
> working towards the right algorithm."

Note the structure of that sentence. The threat is not that the algorithm is wrong. The
threat is failing to admit it. He treats the admission as the load-bearing act.

## The Sega story: telling the customer you cannot deliver, then asking to be paid

Running in parallel with the algorithm crisis was a contract with Sega to build the graphics
for the console that became the Dreamcast. Jensen puts the contract at $12 million. NVIDIA
was building it on the architecture that had just been revealed as wrong.

He flew to Japan and told Sega's CEO, Irimajiri, that the technology did not work and NVIDIA
could not deliver the contract. Then he asked to be paid the full contract anyway, because
without it the company was finished. Irimajiri's reply, as Jensen tells it:

> "So what you're telling me is what I contracted you to do, you can't do, but you would like
> all of the money on the contract."

Jensen said yes, that is exactly right.

Irimajiri paid. Not the full amount: roughly $5 million, per Jensen. That money kept NVIDIA
solvent through the rewrite. Jensen's read on why it worked is that the honesty was the
asset. Irimajiri concluded that Jensen was telling him the truth and that the reasoning held
together, and funded the person rather than the deliverable.

The coda. NVIDIA went public in 1999 at what Jensen describes as a $300 million valuation,
and Sega sold its stake for $15 million. Garry notes NVIDIA is now worth north of a trillion
dollars. Jensen's response: "It's more than true."

Separate two things here. The admirable part is the disclosure: he did not let a customer keep
funding a dead architecture. The unusual part, and the harder one to copy, is the ask. Most
founders would deliver the bad news and consider that the integrity move. He delivered it and
then asked for the whole check. That only works if the relationship and the reasoning both
carry it, and the story does not tell you how to know in advance whether yours do.

## How he learns a field he does not know

This is the throughline from the textbook story to everything after it. His stated sequence:

1. Start from curiosity. He describes his default state as having "a whole bunch of questions
   myself."
2. Filter by consequence. If the answer could matter to someone, and could matter to the
   company, escalate it.
3. Then go as deep as possible. He reads the papers and contacts principal scientists
   directly rather than routing through summaries.
4. Reason to first principles, using a specific pair of prompts he repeats: if this, then
   what? If this can get better, then so what?

That last pair is the useful artifact. The first question propagates a change forward through
a system. The second question tests whether the change actually matters if it succeeds. Run
together they filter out technologies that are real but inconsequential.

## Systems thinking as the durable skill

Asked what matters now, he does not say coding.

> "The most important things is systems understanding. Systems awareness, system design,
> system organization, but systems thinking."

His reason is specific and follows from where agents are going: "most of the low-level things
that have to be done are going to be done agentically anyway." If the implementation layer is
automated, what remains scarce is the ability to hold the whole system in your head.

He gives the actual questions he means by systems thinking, and they are concrete rather than
philosophical:

- What problem are you solving, and what are the constraints?
- Where is the input and where is the output?
- Where does the information come from?
- What is the rate of information flowing in and out of the system?
- What is the binding constraint: processor, memory, or networking?

That last one is the habit worth stealing. He does not ask whether a system is fast. He asks
which of three resources is the one actually limiting it. This is the same instinct that let
NVIDIA co-design across materials, chips, systems, networking, and software instead of
optimizing a chip in isolation.

He uses a surfing image for what this looks like at CEO scale: to him a wave looks like
chaos, but a surfer reads it and stays on top. Charitably, that is a claim that pattern
recognition in a complex system is learnable. Less charitably, it is unfalsifiable and does
not tell you how to acquire it.

## AlexNet, and why he says the important thing was not AlexNet

On the 2012 deep learning moment, his claim is that the object recognition result was not the
insight. The insight was that a deep neural network is a universal function approximator, and
therefore not a computer vision technique but a general method.

The consequence he says he drew: every layer of the computing stack was going to be rewritten,
from processor architecture through middleware, algorithms, and applications. That is why the
company moved into robotics, autonomous vehicles, and scientific computing, domains he says
NVIDIA had "never really done before."

Whether he reasoned this cleanly in 2012 is not verifiable from a 2026 retelling. The pattern
is legitimate on its own terms: when something turns out to be general rather than
domain-specific, ask which layers of the stack it invalidates, not which product it improves.

## Open source as the precondition, not the charity

A short but pointed passage. His argument is that modern computing exists because of open
platforms, and he lists them: Linux, Kubernetes, TensorFlow and, with emphasis, PyTorch, plus
the earlier generation of Caffe, Torch, and Theano. Without those, he says, the mobile cloud
industry would not have happened and modern AI would have had nothing to build on.

Read it alongside the fact that NVIDIA's proprietary software layer is a large part of its
position. He is right that the frameworks were open. He is also describing an ecosystem where
the open layers sit on a stack he owns.

## Agents: controllability is the missing piece, not accuracy

His most useful practical claim on agents is that people are optimizing the wrong variable.

Accuracy does not need to be high. "It could literally be 80%, and then we help it the rest
of the way." What is missing is fine-grained control: the ability to reach into the output
and change one pixel, one triangle, one component, rather than accepting or rerunning the
whole thing.

That reframes the agent product problem. An 80% agent with surgical edit affordances beats a
95% agent that is all-or-nothing, because the first one composes with a human and the second
one wastes the 95%.

Internally, NVIDIA runs agents in sandboxes across the company. Jensen mentions Claude Code
running autonomously in sandboxes throughout NVIDIA, and notes that they deliberately let
people use different tools, naming Codex, Claude Code, Cursor, and Cognition, so the company
learns from more than one implementation. He also gestures at Boris being in the room, which
is Boris Cherny of Claude Code, who spoke at the same event.

On OpenClaw, he describes seeing it and reading it as an operating system rather than an
application: "This is the operating system that's going to hold a large language model." He
says NVIDIA contacted its creator, Peter, and told him "all of NVIDIA's engineers are your
engineers." He names Hermes, OpenClaw, LangChain, and DeepAgent as the layer companies will
use to build domain-specific AI.

He dates his interest in reasoning to early chain of thought work out of Stanford, which he
places roughly eight to ten years before the talk, and says the questions he asked then were
how effective it would be and how well it would scale. Those two questions again.

## Physical AI

He puts NVIDIA's combined robotics and autonomous vehicle business at roughly $10 billion
today and calls it "likely our next hundred billion dollar business." He says the ChatGPT
moment for robots already happened a couple of years ago.

The argument connecting generative video to robotics is the sharpest idea in this section. A
model that can generate video of a hand picking up a glass has learned enough physical
dynamics to drive a robot doing it: "If I could generate video of a hand picking up a glass,
why can't I cause a robot to do the same?" Hence world foundation models, AI that has
internalized the laws of physics, and simulation through Isaac Sim and Cosmos.

He cites Alpamayo, which he calls the world's first thinking self-driving car, and says it
became very good on the order of one to two million miles. The implied claim is a sample
efficiency jump. He gives no baseline, so it is unfalsifiable as stated.

Named users of NVIDIA silicon in this section: Waymo, Tesla, Mercedes.

## Jobs

He separates task automation from job elimination and gives three data points: radiology jobs
up around 20% in recent years even though scan reading is automated, software engineering
jobs up about 10% year over year, and paralegals growing quickly despite legal AI, with
Harvey named. The mechanism he proposes is that productivity increases demand rather than
capping it. The numbers are stated without sources and the definitions do a lot of work, but
the structural argument is the standard one. Treat the percentages as unverified.

## How he runs the company

He rejects importing a management template. The image is a race car:

> "You're building a car that you are going to race. You should adapt the car to you."

The corollary is that the organization is not a fixed asset. He says he is constantly
reshaping business processes so that he personally can be more effective, and that on
succession, when he dies on the job the company will have to be reshaped for the next CEO.
He frames the role itself as service and teaching: empowering people with insight rather
than issuing instructions.

Worth noting what is absent. He does not, in this conversation, discuss the flat structure,
the many direct reports, the absence of one-on-ones, or the mass email practices usually
attached to his name. Those come from elsewhere.

## Resilience, which is the actual answer he keeps returning to

> "Resilience is probably the single most important thing."

His method for it is deliberately small in scope. You do not overcome your life in one
sitting. You overcome the morning. You get through today. He says to let the suffering come
a little at a time rather than simulating all of it up front.

That connects to the phrase he is best known for and uses repeatedly here. "How hard can it
be?" He is explicit that this is not an estimate. He knows it is wrong. Things always turn
out much harder than expected. It is a deliberate cognitive stance, chosen because the
accurate estimate produces paralysis:

> "Don't imagine how hard it's going to be and let all of that turn into anxiety and not
> doing something about it."

Paired with it is the belief he calls the actual superpower: "You believe in your ability to
learn." Under that framing, "how hard can it be" is not optimism about the task. It is
confidence that whatever the task turns out to require, you can go learn it, which is the
same claim the three textbooks make.

## What students should study

Hard sciences and systems, explicitly: physics, chemistry, biology, computer science,
computer engineering, systems thinking. His argument is that low-level implementation is the
part being automated, so the durable skills let you specify and orchestrate rather than type.
He is dismissive of coding as an end skill: solving a problem by sitting at a computer writing
code is, in his view, obviously going to be automated. He also compares chip design across his
career, a thousand transistors when he graduated against a trillion today, and says nobody
would have believed the second number.

---

## What is actually actionable if you are small

Most of this talk is about a company with a balance sheet. These parts transfer to a company
with nine people.

1. Separate the technology bet from the company. Write down which technical assumption your
   product rests on, then ask what you do if it is wrong. The NVIDIA story works because
   Jensen treated the algorithm as replaceable and the company as the thing to preserve. Most
   founders have it the other way round.
2. Set a trigger for confronting reality, in advance. The failure mode is not missing the
   evidence, it is knowing and not acting. Pick the metric now and pick the number that
   means the bet is dead.
3. When you cannot deliver, tell the customer before they find out, and go in person. The
   Sega outcome is not replicable, but the disclosure is. The optionality Jensen got came
   from being the one who reported the failure.
4. Ask which resource is binding. On any system you own, name whether the limit is compute,
   memory, or the network, or in a business context, whether it is people, cash, or
   distribution. Optimizing anything else is theater.
5. Use both questions on any new technology: if this, then what, and if this gets better, so
   what. The second one kills more projects than the first, which is the point.
6. On agents, build the edit affordance before you chase accuracy. Ship something that is
   right 80% of the time and lets a user fix the specific wrong part. That is cheaper than
   the last twenty points and it is what makes the tool usable.
7. Buy the textbook. The literal move in the story is that the gap was closed by three books
   and a decision to read them. When your team lacks a skill, the first attempt should be
   acquiring it directly, not hiring for it or routing around it.
8. Shrink the time horizon when things are bad. Overcome the morning. This is not a
   platitude in the context he gives it, it is a specific instruction to stop simulating the
   full difficulty because the simulation is what stops you.

## Where he is talking his own book, and what is unverifiable

Read the talk with these discounts applied.

- Systems thinking is the durable skill. NVIDIA sells full-stack systems, so the claim that
  system-level design is what matters is also a claim that its product category is what
  matters. Possibly true, definitely not disinterested. The companion advice, that coding is
  automating so you should study systems, has the same shape.
- Physical AI is the next hundred billion dollar business. This is a forecast from the
  vendor who would capture it, delivered to an audience of founders who might build on it.
  The current $10 billion figure is a company disclosure. The hundred billion is a wish with
  a number attached.
- The robot ChatGPT moment already happened a couple of years ago. Stated without a
  criterion. No definition of what the moment was, so it cannot be checked or disconfirmed.
- Alpamayo becoming excellent on one to two million miles. No baseline is given for what the
  previous generation needed, so the sample efficiency claim has nothing to be measured
  against.
- The job numbers, 20% radiology and 10% software engineering. Sources unstated, periods
  unstated, definitions unstated. The direction may well be right and the precision is
  unsupported.
- The founding story is told from the other end of a thirty year survivorship funnel. He
  mentions 35 to 40 competitors and never says how many died doing something similar to what
  he did. Honest disclosure plus a hard rewrite is a plan that also produces failures, and
  you do not hear from those founders at Startup School.
- The financial specifics deserve a check before you repeat them: a $12 million Sega
  contract, about $5 million paid, a $15 million exit for Sega, and a $300 million IPO
  valuation in 1999. These are his numbers from memory, thirty years on. Published accounts
  of NVIDIA's 1999 IPO give a materially larger valuation than $300 million, so at least one
  figure in that set is imprecise.
- "It always turns out much harder than we expect, but go in asking how hard can it be" is
  advice that reads very differently depending on whether you survived. It is a good stance
  for someone with the capital and stamina to absorb the gap between the estimate and the
  reality. It is a worse stance for someone with eight months of runway and no Irimajiri.
