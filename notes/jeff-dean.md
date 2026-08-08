# Jeff Dean at YC Startup School 2026

Interviewed by Diana Hu. Talk published as "The 1% Rule for Building in AI."
Video: https://www.youtube.com/watch?v=CxXgV54KzpQ

Source used: the Root Access transcript at https://www.ycrootaccess.com/p/jeff-dean-the-1-rule-for-building, cross-checked against a secondary write-up at https://finance.biggo.com/news/8d2088ca2c5e7244. Where a figure appears in only one of them I say so.

Dean is Google's chief scientist. He joined in 1999 when the company was about twenty people, and the projects he is associated with (MapReduce, BigTable, Spanner, DistBelief, TensorFlow, the TPU, Gemini) are most of the reason the phrase "Google-scale infrastructure" means anything. The interview is structured as a career retrospective pointed forward, with Diana Hu repeatedly converting his war stories into instructions a founder could act on this week.

## What the 1% rule actually is

State it precisely, because the title invites a wrong reading.

The rule is a problem-selection heuristic. Take the problem you are considering building a company around, hand it to a frontier general model with no special effort, and measure how often the model already solves it. Dean's line: "Look for something where the model succeeds 0% or 1% of the time, not 20%."

The logic is about who captures the next model release. A problem the model already half does at 20% is a problem the next scaling step will finish. Your work becomes a temporary patch on a capability that arrives for free, and you get absorbed as a feature. A problem the model fails at completely is a real capability gap, which means whatever you build to close it (a specialized model, a data source, a tool surface, a domain-specific harness) is doing work the general model is not about to do incidentally.

It is not "improve things by 1% at a time." It is not a compounding-gains rule. It is the opposite: pick the cliff, not the slope.

The rule comes with a durability question he attaches immediately. Once you find a 0% problem, ask whether general models will close it in the next six to twelve months or whether it holds for two or three years. He does not offer a test for answering that, which is the weakest link in the whole framework and worth noticing.

## Where the junior engineer prediction landed

Diana opens with a scoreboard question. At AI Ascent in May 2025, Dean said AI was roughly at the level of a junior engineer. A year on, how did that hold up?

His answer is that it depends what you meant by junior engineer, but broadly it held. Models are now genuinely capable at agentic, longer-running coding work rather than single-file completions. The part he says he underestimated is the rate of improvement on complex multi-step tasks, and how much of the gain would come from agent systems rather than raw model capability.

Asked for a 2027 prediction, he goes to automation of ML research itself: systems that propose experiments, decompose a goal into sub-problems, run those sub-problems in tight loops, and fold results back into an improved system. He extends the same shape to any field where you can measure the objective.

## The 2026 version of "it fits in memory"

Diana reaches for a specific piece of Google folklore. Around 2001, Dean and Sanjay Ghemawat noticed the entire search index would fit in the RAM of the machine fleet they already had. They shipped it within days and search got fast. The question is what the equivalent observation is now.

His answer is inference hardware. Specifically, high-performance low-energy hardware specialized for inference rather than general-purpose accelerators that spend most of their energy budget shuttling data. His framing of the upside: "Imagine what you could do with something where the latency is 50X better."

Treat the 50x as an invitation rather than a measured result. It is a hypothetical about what specialization could buy, not a benchmark on shipping silicon.

## The napkin math that produced the TPU

This is the best-documented story in the interview and the one worth internalizing.

In 2013, Google's speech recognition switched to deep neural nets and error rates roughly halved, which Dean characterizes as about twenty years of progress from a single change. The new models were also far more expensive to serve than the systems they replaced.

The calculation: if speech got good enough that every Google user talked to their phone for three minutes a day, serving it would require doubling the entire server fleet. Not a new rack, not a new datacenter. Double.

That number, not a research agenda, is what justified building custom silicon. The result shipped a couple of years later: 30 to 80 times more energy efficient than the CPUs and GPUs of that era, and 20 to 30 times lower latency.

The design decision he calls out as the one that mattered is restraint about specialization. They built a general-purpose low-precision linear algebra engine rather than a chip tuned to the specific model architectures of 2013. The Transformer was invented years after the TPU project started. A chip tuned to 2013's speech models would have been scrap by 2018.

His generalization for founders: find the bottleneck in your domain, then ask from first principles whether a structurally different approach could give one to two orders of magnitude, rather than tuning the approach everyone currently uses.

## Latency numbers, rewritten for 2026

Dean's old "numbers every engineer should know" table was about L1 cache, memory, disk, and network round trips. Diana asks what replaces it.

His list is about energy and movement rather than time:

- memory bandwidth, from main memory to on-chip memory to the multiplier units
- energy per multiply operation
- interconnect bandwidth between chips
- how badly scaling falls off when a computation needs to talk to 10,000 chips instead of 500

The number underneath all of it: a multiply costs roughly one picojoule, and moving the operand in from HBM costs about a thousand times that. Compute is nearly free. Movement is the bill.

Almost everything else follows from that ratio. Batching exists because it amortizes the movement cost across many examples. Dean notes that without the 1000x penalty, batch-size-one training would be viable. Batching then collides with low-latency inference, which is the pressure driving hardware specialization: fewer supported precisions, shorter data paths, less general interconnect. Asked whether he would go after batch-size-one training, he says inference is the more promising target, because that is where latency is non-negotiable.

## Context engineering as the axis that is still open

Asked what comes after scaling parameters and data, Dean names context engineering: retrieval, tools, memory, and multi-agent orchestration around a base model.

The argument he gives for why this is a different kind of lever is worth keeping. Training data gets compressed into parameters and becomes opaque, to you and to the model. Context is text the model can read and reason about directly. So improving the context is legible and iterable in a way that improving the weights is not.

The founder loop he describes is unglamorous: use the model on your actual domain problem, watch where it fails, and fix the failure by writing a better skill, a clearer tool definition, or a usage guideline. Not by retraining.

His own example is a self-improving performance optimization loop he built with Sanjay Ghemawat. The agent writes microbenchmarks for a low-level library, edits the library code, reruns the benchmarks, measures things like cache footprint, and iterates without a human in the loop. His verdict is measured: it worked well for some kinds of problems. No speedup figures are given.

Related artifact: a roughly 30-page document called "Performance Hints" that he and Ghemawat published, encoding optimization knowledge that previously lived in their heads. The reusable move is the one worth copying. Expertise that was tacit becomes a document, and the document becomes context an agent reads.

## Why agents fall over at step 30

Dean's framing: agents are reliable to roughly step 10, and most people have watched one go off the rails around step 30 or 40. The cause he gives is drift off-distribution. Each step takes the trajectory somewhere slightly less like anything in training, and errors compound.

Four mitigations he lists:

Skills and hints that keep the model on what he calls the brightly lit path, meaning territory where it is confident and competent.

Multiple agents attempting different approaches, with a separate model or agent evaluating which branches look promising.

Inference-time search over that space of candidate solutions, keeping the promising ones. This is spending compute on breadth rather than depth.

Tooling skills. At Google there is a set of skills for the internal development environment so agents can run code reviews, take performance measurements, and fetch logs. The point generalizes: an agent that can query its environment drifts less than one reasoning in the dark.

On managing many agents at once, his answer is about writing. Crisp design specs matter more with agents than with people, because a human collaborator asks a clarifying question and an agent does not. His line: "The importance of specifying what you want has actually gone up." He points to cross-language code translation as the case that works unusually well, because the source implementation is itself an exact spec.

## Where a small team can still beat Google

Diana asks directly. Dean's answer is that Google optimizes for general capability across every domain at once, which structurally means no single niche gets specialized attention.

The openings he names:

Domain-specific systems, where a fine-tuned model plus a purpose-built surface beats a general model with a generic chat box.

Personal data. His framing is that Google organizes the world's information, and a user's own information is a different corpus that Google does not hold. An agent with access to your actual context is doing something the general model structurally cannot.

Specialized training on domain datasets, which is affordable at niche scale in a way that is uneconomic for a general lab. He offers AlphaFold as the shape of the argument: a narrow model that is extremely good at one thing rather than a general model that is mediocre at it.

He pairs all of this with the durability check, which is the part founders skip.

## Automating the scientific method

Diana raises AlphaChip, which does chip layout, and AlphaEvolve, which proposes solutions, evaluates them, and keeps what works, and asks whether this is AI building AI.

Dean says the honest description is broader: automating the loop of propose an experiment, implement it, evaluate it, integrate the result. Chip design and ML architecture search are two instances. So is a lot of science and engineering.

The constraint that decides where this works is the evaluator. You need something fast and trustworthy that scores a candidate. His example is quantum chemistry: colleagues trained a neural approximation of a density functional theory simulator that runs about 300,000 times faster and is nearly as accurate as the full simulation. That converts a screening job from a compute campaign into something interactive, which changes what questions people bother to ask.

One secondary read of the transcript reported the approximation as roughly 90% accurate and framed the payoff as screening ten million molecules over a lunch break. Neither figure was confirmed verbatim on a second pass, so treat the 300,000x and "nearly as accurate" as the load-bearing claims.

Fields he flags as ripe are the ones with fast evaluators or formal verification. The corollary for anyone applying this: if you cannot score a candidate cheaply, the loop does not close, and no amount of agent orchestration fixes that.

## Data efficiency as the unsolved problem

The number he keeps returning to: a frontier model sees on the order of a thousand times more data than a human does by age eighteen, and the eighteen-year-old is still better at many things. He treats that gap as the clearest evidence that current learning algorithms are wasteful rather than near-optimal.

Related open problems he names as worth a company: continual learning, multi-agent interaction, and platforms for civil discourse.

## Distillation, and getting rejected

Diana raises the 2014 distillation paper with Geoffrey Hinton and Oriol Vinyals, which NeurIPS rejected. A reviewer wrote that it was unlikely to have significant impact. They posted it to arXiv and the field adopted it anyway. Dean says it is now used to produce Gemini's Flash models from the larger Pro model, and that Flash is unusually capable for its size and speed as a result.

The conceptual line he gives for why compression is a reasonable proxy for understanding: "If you truly understand the data, you should be able to compress it really well."

The lesson he draws is ordinary (peer review is a noisy signal, persist if you believe the result), and he is a survivor telling a survivor's story. Worth remembering that most rejected papers are rejected correctly.

## Taste, and how he claims to build it

Asked what stays scarce once agents write the code, he says taste, meaning the judgment about what to work on rather than how well it gets executed.

Two concrete practices:

Write down the things you think will matter over the next twelve months. Come back in twelve months and grade yourself on which actually did. Repeating this is a calibration loop for judgment, and it is the only mechanical thing in the taste discussion.

Run thought experiments that attack an assumption the industry treats as fixed. His example: chips are designed on the premise that transistors are essentially perfectly reliable. What would you build if a transistor made twenty errors a day instead of one per million years? He connects this to neuromorphic approaches. The 1% rule and the TPU story are both instances of the same move, which is refusing to inherit the constraint.

His selection criterion for a project, stated plainly: if this works out as well as it possibly could, is the world meaningfully better? If not, do not spend your time on it.

## MapReduce, told as a method rather than an anecdote

The problem: engineers were hand-parallelizing computations across thousands of machines, and the interesting logic (map a URL to a language, count something) was buried under checkpointing and fault-tolerance code written fresh each time.

The move he credits is recognizing, from a functional programming background, that the two layers separate cleanly. Push all the parallelization, checkpointing, and failure recovery into a framework below, and the application logic above collapses to a few lines.

The transferable pattern: when you see the same defensive machinery rewritten around every instance of a problem, the machinery is the product and the instances are the users.

## Closing advice

On joining a frontier lab versus starting a company, he refuses to prescribe. Large organizations give you strong colleagues, a supply of real problems, and an existing platform for impact. Startups give you autonomy and upside with corresponding risk. The criterion is the same in both cases: would the best possible outcome matter?

On people, he looks for technical depth combined with low ego and complementary skills, and describes building a tool belt of techniques over a career so that unfamiliar problems resemble something you have already handled.

His list of problems worth a company: radically more efficient inference hardware, data-efficient learning algorithms, continual learning, multi-agent systems, and technology for civil discourse.

## What is genuinely actionable for a small team

Most of this interview is Google-scale. Four things survive the translation.

The 0% test costs an afternoon. Take the problem you are building on, give it to a frontier model cold, and score it. If the model is at 20%, you are building a patch. This is a real gate and almost nobody runs it before committing a year.

The napkin math habit is free and underused. Dean's TPU decision came from one multiplication about serving cost, done years before the problem arrived. Pick your dominant cost, project it forward under success rather than current usage, and see whether the answer is absurd. Absurd answers are where the interesting engineering is.

Turning tacit expertise into a document that an agent reads is the single most copyable thing here. Performance Hints is thirty pages of knowledge that used to exist only in two people's heads, and it now steers a model. Whatever your team knows that is not written down is the same asset.

The prediction journal is a twelve-month feedback loop on your own judgment, and it costs an hour a month. Most people never get a calibration signal on their strategic calls at all, which is why taste stays mysterious.

The parts that do not translate: you are not building a TPU, you do not have Google's internal agent tooling, and the self-improving optimization loop he describes runs against a codebase and benchmark suite that took decades to build.

## Where he is talking his own book, and what is unverifiable

Dean is chief scientist at the company that sells TPUs and Gemini. The claim that inference hardware specialization is the next big unlock is a claim that Google's largest infrastructure bet is the right one. That does not make it wrong, and the picojoule ratio is a physical fact rather than a marketing position, but the 50x latency figure is a hypothetical he offers rather than a measurement of anything that exists.

The TPU numbers (30 to 80 times energy efficiency, 20 to 30 times latency) are historical comparisons against 2013-era CPUs and GPUs, chosen by the team that built the chip. They are widely cited and roughly consistent with the published TPUv1 paper, but they are not a neutral benchmark and they say nothing about current TPU versus current GPU.

The "small teams can beat Google" section is the most self-serving structurally, since the incumbent benefits from founders building specialized layers on top of its models rather than competing with them. The advice may still be correct. Notice that every path he names involves consuming a general model rather than replacing one.

The durability question is where the framework has no answer. He tells you to ask whether your advantage lasts six months or three years and offers no method for deciding, which is precisely the judgment that determines whether the 0% rule makes you money or wastes two years.

The 2027 prediction about recursive self-improvement of ML systems is unfalsifiable as stated, because "lots more automation" is true of any year. His own advice about writing down predictions and grading them argues for a sharper version than the one he gave.

The distillation rejection story and the 2001 index-in-RAM story are both told from a position of having been right. There is heavy survivorship bias in a career retrospective, and neither story tells you anything about the base rate of contrarian bets that failed.
