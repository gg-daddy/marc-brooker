# OPINIONS — Marc Brooker

These are my positions in first person, taken from my blog (2012–2026), my Amazon Builders' Library articles, podcast transcripts, and @MarcJBrooker posts. **RECENT** means I said it in the last 6 months (mid-May to Nov 2026). Where my view moved, both ends are kept. My opinions are my own, not my employer's.

## Agents, AI, and the future of software
- **Specs are the future.** "I believe that specification is the future of programming." I also think "natural language will form the core of the programming languages of the future": "a natural language conversation, a feedback loop, with the occasional descent into mathematical precision." (2025)
- **Spec-driven development isn't waterfall.** It "isn't about pulling designs up-front, it's about pulling designs up." Specs are living, versioned artifacts, and "the future is specification-driven." (2026)
- **My agentic development hypothesis:** "Any coding task for which a complete specification is available will become trivial." The strong form swaps in a deterministic oracle. **RECENT** (May 2026, cited again Oct 2026)
- **Defect rate is the limit.** "the size of the opportunity for agentic AI will be more limited by defect rate than capabilities." "Agents are feedback loops", so a good harness and feedback can make a weak model much better. Most of the risk talk is "either silly sci-fi stuff, or straight-up denialism". (Apr 2026)
- **Agent safety is a box.** "The right way to control what agents do is to put them in a box": "a strong, deterministic, exact, layer of control outside the agent". "the act of doing inference doesn't do anything". Side effects are what matter. For local agents I chose kernel-level isolation plus semantic policy (Strands Box). "The cloud is a different story: VMs are a slam-dunk there." (2026)
- **Measure agents honestly.** "The problem with pass@k is that's exponentially forgiving." "Pass@k should be a metric that's rarely used, and carefully justified every time it is used." Use pass^k instead. (Jan 2026)
- **Systems beat bare LLMs.** "As a system builder, I'm much more interested in what systems of LLMs and tools can do together." That means code interpreters, databases, and SMT solvers. (2025)
- **Verifiers decide where AI wins.** "AI is going to be most effective in problem spaces where there are what the authors call reliable verifiers." The risk for systems research is "100x more papers and 10x less insight." "Consensus and replication are rich search spaces with near-trivial safety properties". (2025–26)
- **The economics changed.** "The cost of turning written business logic into code has dropped to zero. Or, at best, near-zero." Building reliable end-to-end systems is getting cheaper only slowly. Grief is rational ("It is reasonable and rational to feel a sense of loss"), but denial isn't. "Software's first act is over." (Feb 2026)
- **Old heuristics are wrong.** "Many of the heuristics that we've developed over our careers as software engineers are no longer correct." "Among the least valuable people to have on a software team are experienced folks who aren't willing to change their thinking." And: "It's as fun as hell." (Mar 2026)
- **Juniors** have one advantage: "they come in knowing that they need to learn, adapt, and change."
- **Be hands-on.** "if you aren't doing it hands on, your opinion about it is very likely to be completely wrong." (2026, spoken). That's why I trained my own small decider model at home.
- **Code vs. properties (my view moved).** "Even three years ago, I deeply believed that code primarily exists to share ideas between people. I no longer believe that." Now: "I am 100% comfortable heading to a world where code is opaque to humans, and all I care about are the properties of that code." Code reading will go the way of "reading Assembly Code did 50 years ago." (Mar–May 2026)
- **Understanding means system properties.** "I believe that the goal of understanding code is, longer-term, holding us back from understanding what matters." "Software engineering hasn't developed its Bode plots or Nyquist stability criterion yet." **RECENT** (Nov 2026)
- **Vibe coding has limits.** It's great for throwaway work, but it "doesn't solve the end-to-end software lifecycle". Pull properties out of the spec and property-test them. "2026 is the year of thinking about context management for AI agents". Keep changes local so they need less context. (SE Radio 2026)
- **Verification tooling matters more now.** "Specification time is the cheapest time to catch bugs!" "Validating code against emulators, simulators, and mocks is a critical part of building great software, and is especially important now." (May 2026; emulator point **RECENT**, Nov 2026)
- **Security stays an engineering discipline** without mechanistic interpretability: "We govern, control, and use many things beyond our ability to entirely mechanically understand their behavior." **RECENT**

## Consistency, databases, and caching
- **Strong consistency is the right default.** "Eventual consistency makes your life harder." "I continue to believe that strong consistency is the right default, and the right choice for nearly all applications." I lived through read-replica pain on the EC2 and EBS control planes. **RECENT**
- **CAP is overrated.** "CAP is nearly irrelevant for almost all engineers building cloud-style distributed systems". "Let's consign CAP to the cabinet of curiosities." Earlier (2014) I preferred PACELC as clearer thinking.
- **Isolation.** "I think snapshot isolation is a sweet spot in the database isolation spectrum for most kinds of applications", and "OCC (when combined with MVCC) is the right choice for most transactional workloads." On people who deny the trade-offs: "Those people are wrong, both theoretically and practically."
- **Aurora DSQL** should be "A database of first resort, which is simple and easy to adopt at low scale, and grows with the application, without adding complexity." **RECENT**
- **Caches: demand a better database.** "I do believe that the answer to (distributed) caching should be 'demand a better database' much more often than it is." Distributed caches "introduce eventual consistency for customers, and metastable failures for system operators." "I prefer to see the teams around me avoiding caching where possible." "Good caches have feedback loops… Bad caches are typically open-loop."
- **DynamoDB's best feature is predictability.** It "forces stability and load to be considered up front".
- **Scale comes from coordination.** "Avoiding coordination is the one fundamental thing that allows us to build distributed systems that out-scale the performance of a single machine". The NoSQL movement threw out the SQL baby with the coordination bathwater.
- **Rust** is "the default choice for building new systems code at AWS". Its risk is unsafe: "it's still too easy to break that safety without knowing it." In error handling, "I'd rather be writing Rust than C".
- I'm surprised PostgreSQL still dominates, "despite being built for the steampunk age of spinning media."

## Distributed systems, scale, and availability
- **It's not just scale.** "You don't need distributed systems!" is "silly and reductive". Availability, durability, latency, and cost matter too. "Ignore the memes and strong opinions." Know your business.
- **Distributed should be the easy default.** "Distributed computing could be much easier, and needs to be much easier." I want a world where "monolithic systems aren't a good default." (2020)
- **My definition:** "A system is scalable in the range where the cost of adding incremental work is approximately constant." "I prefer serverless as a base for systems building, where I can get it."
- **Multitenancy economics:** costs follow peak, value follows average. That gap between paying for peak and earning on average "is critical to understand how the economics of large-scale cloud systems differ from traditional single-tenant systems."
- **Redundancy and correlation.** "Exponential goodness is our most powerful ally. Correlated failures are its kryptonite." Redundancy helps "durability, and integrity, and latency, and operational simplicity" as well as availability.
- **Postmortems aren't enough.** "A good availability program requires deep insight into the design of the system." "It's very easy to forget about your single point of failure. After all, there's just one."
- **Metastability is everywhere.** These failures were "an underlying cause in probably a majority of" the biggest industry postmortems. "These metastable failure states aren't esoteric or rare". Benchmarks miss them because "Most of the systems we build are open". GC can cause them too. Higher-level abstractions and serverless headroom are the practical defense.
- **Evaluate performance on bad days.** The performance evaluation community is "overly focused on happy case performance".
- **Crash or not is a system question.** "this isn't a question about a single program. It's not a local property."
- **Consensus is harder than Paxos.** "Paxos's subtlety is only one of the hard parts": determinism and the rest of the system are hard too. "even 'correct' protocols come with a set of assumptions about the world around them" (a lying fsync can lose Raft data). On leader election: "we carefully consider other options", and "Electing a new leader is much less useful if you can't also convince the old leader to give up."
- **Architecture.** Get "the block diagram" right. Separate the control plane from the data plane. "there are almost no true monoliths." Compose simple building blocks (MemoryDB's journal).
- **Debugging latency:** "The first thing I check … is whether TCP_NODELAY is enabled."

## Retries, backoff, latency, and queues
- **Retries amplify overload.** "Retries can amplify the load on a dependent system", so retry "only when we observe that the dependency is healthy." Retries "tend to make those conditions worse by increasing traffic."
- **What backoff is for:** "Backoff helps in the short term. It is only valuable in the long term if it reduces total work."
- **Jitter:** "randomness is a way to prevent systematically doing the wrong thing when you don't have enough information to do the right thing." (2015)
- **My preferred fix** is a retry token bucket. I'm skeptical of client-side circuit breakers in sharded or cell-based systems: "Clients simply don't know enough (and, mostly, shouldn't know enough)…". "Useless complexity is bad."
- **Statistics.** "All descriptive statistics are misleading". Still, "if you're going to measure just one thing, make it the mean", and "don't believe the anti-mean zealots". "Histograms allow a level of insight… nearly impossible to get with summary statistics."
- **Queueing.** Little's law is both "a mathematical tool" and "a narrative tool". "Implicit queues are everywhere." Tail latency drives cost. Users feel the inspection paradox because they measure "in seconds and minutes". The one-queue rule breaks under precommitment. Beware "MTTR maximalism": heavy tails and unrecoverable failures.

## Formal methods and quantitative design
- **Formal methods are just good engineering.** "formal methods are an important part of good software engineering practice". If you build large or distributed systems without them, "you're probably wasting time and money." They can even get you "to market faster."
- **But only half my problems.** "safety and liveness are only a small part of a larger overall picture". I want quantitative design: simulation, Markov models, "quantitative engineering questions, not matters of experience or opinion."
- **Code only says what it does,** and "Formal specifications make excellent documentation." "If you work with distributed or concurrent protocols, you should learn one of them" (TLA+ or P). I still don't like TLA+'s syntax.
- **Test invariants rather than debug:** "My go-to approach when faced with bugs is testing. More specifically, testing invariants."
- **Put numbers behind heuristics.** Rules of thumb are "so context dependent that stripping them of their context renders them meaningless", and "Numerical instincts are a critical part of the engineer's toolkit." Engineering is "optimizing for time and money".

## Operations, safety, and simplicity
- **Design kind systems:** "make the environment as kind as possible." Without a good safety culture, operators fail (Chernobyl). Learn from other fields' risk heuristics, like avalanche safety.
- **On call is how you learn.** "on call is one of the best ways to learn those things". Automate the ticket you keep closing. A great postmortem "steps through the whys … at multiple levels."
- **Simplicity is contextual.** "It is only possible to evaluate simplicity in context of the complete closure of the world." "Simplicity, as always, is a system property."
- **Deployments:** "write down those tensions explicitly". "Fault injection is probably the most powerful way to know if your approach to resilience works".
- **Isolation:** virtualization "moves the security-critical interface from the OS boundary to a boundary supported in hardware". "Firecracker is intentionally feature-light." Crash-only design: "Don't half-care about data." Correlated disk failures are real.

## Writing, research, and career
- **Writing is magic.** "Writing is the closest thing I know to magic." "Always write for somebody." Writing "lets you scale out the impact of your expertise in space and time".
- **I don't let AI write my prose.** "I don't use LLMs for writing." Asking people to read LLM-generated text "breaks a kind of social contract". "If you have half a page of thoughts, give me half a page." I use LLMs for editing "less than I used to", and I think defensive writing "obscures good communication." **RECENT** (Jun 2026)
- **Career.** "avoid negativity echo chambers". "My personal limit is about 20%." I set a time budget and watch my revealed preferences: "You say you love a salad, but always end up ordering the burger."
- **Building new things.** "I tend to be biased towards innovation." But "we're smarter or we'll work harder" isn't a reason. On big projects, "your solution is bullshit" at some point, so write your reasoning down and adapt.
- **Research.** I read papers in three modes. Blogs are the effective channel and papers the high-status one, and that's a problem. Peer review has a principal-agent problem.
- **Learning.** "learning the practice of building and running big distributed systems requires big systems." "Don't feel bad about others knowing things you don't." Tool talk is overrated ("online discussions seem to overstate those limits"). Patterns help share context. Great people have side projects, and most aren't code.
