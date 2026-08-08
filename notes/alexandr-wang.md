# Alexandr Wang at YC Startup School
### Detailed notes

Interviewer appears to be Garry Tan. Wang is now at Meta Superintelligence Labs, roughly one year in, after founding Scale AI at 19.

A note on the transcript: it is auto-generated and garbles several proper nouns. "Los New Mexico" is Los Alamos. "Palunteer" is Palantir. "Freriedman" is Jared Friedman. "aruck" is awestruck. "wrong jobs" is cron jobs. "slashgoal" is /goal. The Meta model names come through inconsistently as Museark, Musepark, Muse Spark, and Morg, so treat specific version numbers as unreliable.

---

## Origin story

Grew up in Los Alamos, New Mexico. Describes it as the middle of nowhere, now Oppenheimer-famous. Did math and computer science competitions throughout school.

Knew he wanted to do big things without knowing the path. A friend who was deep into programming and interned at Palantir became the influence that pointed him toward the Valley.

The sequence: worked at Quora for a year straight out of high school as a gap year, then MIT, then Scale at 19. He gives ages inconsistently in the transcript, saying he was 19 at Quora and 18 at MIT, which cannot both be right in that order.

On the period from 17 to 19, he says what he wanted to do was constantly changing and he felt like he was drinking from a firehose, mostly learning from the people around him.

Two things he recommends from that stretch. Working at a company first, because from the outside you have no idea how companies actually work, what it takes to build something, what iterating looks like, or how groups of people make decisions. And going to MIT, because it gave him room to explore what was interesting. He trained his first models there, played with TensorFlow the year it came out, and that is where the idea for Scale came from.

Applied to YC after one year at MIT. Says getting in felt like a miracle. His summary of YC's value is that it blends real support with people willing to tell you when you are being a dumbass.

---

## The pivot that produced Scale

The YC application idea was an AI agent to help people get medical care. He notes the irony that this is exactly the kind of product that exists now, and calls it a good idea with wrong timing.

They worked on it a month or two before Jared Friedman pulled them aside and said he did not know if it was going anywhere. Wang's read: that was exactly what they needed to hear.

Then they went back to the drawing board and reasoned from what he already knew about training models.

The reasoning is worth stating precisely, because it is the most transferable thing in the talk. Training a model required three inputs: compute from a cloud account, code to run the training, and a dataset. Two of the three you could get by pressing a button online. For data there was no effective way at all. From that gap it felt obvious that a press-a-button way to get data was coming.

He points out you could not have arrived at Scale by reading what was hot. Data stayed unsexy for years afterward. Even with good revenue, investors kept asking whether it was a real business, whether it had longevity, whether it was durable. His explanation is that none of them had ever trained a model. The same investors who passed now write think pieces about data being one of the biggest opportunities in AI.

---

## Conviction

His central claim about company building: you need conviction in a set of beliefs nobody else agrees with.

The pattern he sees in successful companies is that they started long before the core idea was popular, then toiled in obscurity for years before the idea became consensus. Success requires identifying truths about the world early.

The failure mode is following the herd. His words are that you will get immensely confused and end up nowhere. You have to develop your own compass for what the future looks like, because everyone else will just confuse you.

On execution mechanics, he is deflationary. Nobody is good at starting a company when they start a company, because nobody is good at something they have never done before. Investors who met him early told him afterward that he grew and changed fast and they had not seen it at the time. He thinks that is true of essentially everyone. His framing: you start out bad at everything, and the whole game is how fast you improve.

---

## Starting a company now

The bottleneck is not model progress. It is diffusion, meaning getting the technology through the rest of the world and helping the world adapt. His counterfactual: if models stopped improving today, there would still be decades of upheaval in the economy and how the world operates.

He calls this a once-in-a-civilization opportunity to be a dreamer, have ambition, and impose a view of how the future should look by building something.

The competitive framing changed. Ten years ago starting a company was David versus Goliath and you had to be clever, find an angle, and compete with fewer resources. Now he thinks it is closer to Goliath versus Goliath, with the startup as a mecha-Goliath amplified by agents while incumbents are the traditional kind. His claim is that a startup that properly embraces agents and leverages its strengths ambitiously can outcompete incumbents easily.

---

## What superintelligence means operationally at Meta

References a memo Zuckerberg wrote about personal superintelligence roughly a year prior.

The belief: every one of the billions of people in the world will have a superintelligence adapted to them, that knows their context and helps them accomplish their goals.

The organizing concept is agency expansion. The question he says they think about is how to help people accomplish things they could never have dreamed of, and what everyone in the world would do if everything were easy.

He explicitly rejects a totalizing or totalitarian view where AIs control the world, in favor of AI enhancing a broad ecosystem.

The concrete version is an entrepreneurship explosion. There are about 200 million businesses on Meta platforms today and he thinks that should become billions. The end state he describes is a dynamic ecosystem of business agents interacting with personal agents.

---

## Running a frontier lab

He has been at Meta about a year. Says publicly that Llama was not on the trajectory Meta needed, so he ran a zero-based build of a frontier lab, using much of what existed but rethinking the structure. Nine months later they shipped their first model, then an image model and a point release two months after that.

What struck him:

Talent density was the core bet, and it compounds naturally, because the more talented people you have the more the most talented people want to join.

Frontier AI work is research, not product engineering. It requires a different mindset and operating model than internet companies, weighted toward experimentation, science, and scaling.

The goal is to build the lab as an organism that can compound alongside exponential growth in capabilities, compute, adoption, and usage all at once.

Roadmap items he names: continued updates to the Spark line, bigger models he thinks will compete with the best available, a harness of their own coming soon, and open-source models. The stated philosophy is a decentralized world of AI capability.

---

## Cost and the case against rationed intelligence

Tan reports that Spark was as good as Opus for agentic flows with skill files while being roughly 8x cheaper.

Wang's position: they do not believe in a world where models are expensive enough to be rationed to the wealthiest developers and companies.

This matters more than it sounds, and connects directly to his agentic looping argument later. If the play is spending 1000x more tokens on a single outcome, then price per token stops being a line item and becomes the constraint on whether the loop is viable at all.

---

## Every wave is 10x the last

His history of AI product waves, each roughly ten times bigger than the previous one:

Self-driving cars came first, which he calls genuinely cool but small by comparison. Then large language models and chatbots, about 10x bigger. Then coding agents a few years later, about 10x bigger again.

His conclusion is that new modalities and form factors will keep arriving, each dramatically bigger, and that the best AI products have not been built yet.

---

## On harnesses

Tan's framing, which Wang does not dispute, is that current harnesses are Ferraris that break down on the side of the road all the time. Tan names OpenClaw and Hermes agent as things he still uses.

What Wang says they are optimizing for: speed first, because for anyone using these tools speed is among the most critical things. Reliability second. Extensibility, so the harness scales to whatever complexity of multi-agent setup you want.

The line worth extracting: he thinks a great deal of innovation will happen above the harness, in how you orchestrate agents, set up loops, and develop complex ecosystems of agents working together. He wants models that plug into every available harness to maximize combinatorial innovation, rather than a single vertically integrated stack.

---

## The alpha, stated directly

Asked for near-term applications people have not figured out, his answer is agentic looping.

The specific claim: there is astronomical opportunity in developing systems that let you spend 1000x or even 1,000,000x more on tokens to drive a single outcome inside a continuous feedback loop.

His model of a company is a large-scale feedback loop with humans operating each edge. Get customers, make them happier, they spend more, you hire more people, who get more customers and make them happier. Inside that outer loop are many micro feedback loops.

The opportunity is building agentic systems that operate and optimize those loops.

The condition he attaches is the whole thing. In his words, if you can develop the right agentic loop and you have the right eval or the right metric for the agents to optimize, a swarm of agents can accomplish more than a team of 100 engineers, very easily. The metric is what makes the swarm work. Without it you have expensive noise.

---

## The mechanics are mundane

Tan asks whether it really is just markdown files and cron jobs, plus pointing the agent at enough data to figure out something out of distribution. Wang confirms.

His list: figure out the metric, then skills, markdown files, cron jobs, and /goal.

His comment on this is that it is always funny how mundane everything is once you dig in.

When Tan mentions LinkedIn threads claiming there is magic involved, Wang's response is to ignore LinkedIn. Tan's addendum is that LinkedIn is where you get customers.

---

## What people are missing right now

He thinks the dominant debate, meaning how good models are really getting, whether we hit a wall, whether superintelligence is two years or five, is largely a waste of time, because powerful models are inevitable either way.

His framing is the exponential. A decade ago the best models recognized cats in YouTube videos. He says you cannot look at the last decade and not be awestruck.

What will be obvious in hindsight is that intelligence became abundant and agency became abundant.

The consequence he draws is a real change in what is scarce. For all of human history, groups of smart people coordinating toward a shared goal was the bottleneck on progress. He uses the founding of the United States as the example, and says it is also the story of nearly every American company and every YC company. That changes. Intelligence and agency stop being scarce, and vision and ambition become scarce instead.

The test he poses: do you have a clear view of how the world should look in five to ten years that differs from today, and the drive to go through all the crap to make it happen.

He balances this with responsibility. The world is barely ready for the technology. Builders have to help enterprises and governments adapt, and help figure out biosecurity and cybersecurity. On the other side sit new sciences, long-unsolved problems in health and biology, businesses and creative work that could not previously exist.

---

## Career advice for people learning now

Systematic and rigorous thinking still matter, because the abstraction layer keeps moving. He says he did not used to believe it would play out this way.

The ladder he describes: his era started by writing code, then organizing humans. Now you orchestrate one agent, then figure out how to orchestrate armies of agents, then a million, then a trillion. Each rung still requires structuring workflows at whatever abstraction layer you happen to be at.

His verdict is that systems thinking never goes out of style, and going all-in on word cell over shape rotator is a mistake. You still need to shape rotate.

What he adds on top is a deeper compass and philosophical view of how the world should develop, since humanity will change more in the next decade than in the last hundred years, and coherent positive visions for that matter more than ever.

On the Stanford CS enrollment drop that Tan raises, Wang does not endorse the retreat. Tan's own objection is that you still need those skills to build good agents.

---

## Closing

His message to his 18-year-old self has two parts.

Develop your own internal compass for how the future will develop, and hold strong conviction in it, because you will be inundated with noise and it is especially hard to have conviction when you are young and lack experience. He says it took deep conviction in what they were building to weather years of chaos in the market, the industry, and among the people around them.

Second, identify the exponential with both the steepest curve and the longest runway. Decades ago that was Moore's law. Right now he thinks it is AI progress, and there will be more such curves later. It is fine if the starting point looks boring or uninteresting. Cat detectors in YouTube videos were hard to sell as the most important technology of our time, but they sat on an unbelievable exponential.

Ends by announcing $1,000 in free Spark API credits for the room.

---

## My read on what is actually actionable

Three things in this talk carry weight beyond the genre conventions of a founder interview.

The Scale origin reasoning is a reusable method. Enumerate the inputs a process requires, check which ones are already one-click, and build the missing one. That is a repeatable search procedure, not a story about being smart.

The metric-plus-loop claim is the operational core, and it converges with what Anthropic says about verification from a completely different direction. Both arrive at the same place: an agent swarm without an oracle produces expensive noise, and the oracle is the thing you build first. Wang frames it as an eval or metric to optimize. Anthropic frames it as ground truth from the environment. Same constraint.

The cost dimension is underrated. If the strategy is 1000x more tokens per outcome, cost per token is not a procurement detail, it is what decides whether the loop closes. Worth noting he sells a cheap model, so he has a reason to emphasize this, but the logic holds independent of who is making it.

## Where he is talking his own book

Worth reading with these in mind. He is announcing a Meta harness soon, so "innovation happens above the harness" is a convenient position for a late entrant. The 8x-cheaper-than-Opus comparison comes from the interviewer rather than a published benchmark. The Llama-was-off-trajectory admission is safe because it is already public and predates him. And the "every wave is 10x" framing is unfalsifiable in the direction that matters, since it always predicts the next thing is bigger.

## One place he disagrees with Anthropic

Wang describes the loop as needing scaffolding you build: skills, markdown files, cron jobs, a metric. Boris Cherny's advice is to delete your scaffolding on every model release and add back only what you observe the model repeatedly failing without.

They agree completely on the feedback loop and the metric. They disagree on how much written structure should surround it. That disagreement is empirical and testable on your own work, which makes it more interesting than either position taken alone.
