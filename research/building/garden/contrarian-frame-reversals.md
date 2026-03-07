# Contrarian Frame Reversals: Building Complex Things and AI

## The Kariko/Feynman Method Applied

What follows is a systematic inversion of dominant framings about how we build complex things and how we build AI. Each reversal takes a standard assumption, flips it, and argues the strongest possible case for the inversion using real-world evidence.

---

## Reversal 1: Tool becomes Subject, Subject becomes Tool

### Standard Framing
AI is a tool that engineers build, deploy, and control. Humans are the subjects -- the architects, the principals, the ones with agency. We design AI, we train it, we ship it, we use it.

### Inverted Framing
AI is a subject/environment we cultivate, and engineers are increasingly the tools -- the instruments through which AI systems grow, reproduce, and refine themselves.

### The Strongest Case for the Inversion

Consider what actually happens in modern AI development. In RLHF (reinforcement learning from human feedback), thousands of human labelers spend their days adjusting their own judgment to match what the system needs. The labelers experience "drift in judgment" and reshape their cognitive patterns to serve the training process. Who is training whom? The humans are literally reshaping their minds to become better instruments for the AI's development.

The shift is already visible in engineering roles. As CIO reported in 2026, engineering roles are being redefined "from creators to curators" -- engineers spend less time writing foundational code and more time "orchestrating a dynamic portfolio of AI agents." The human is not the architect anymore; the human is the gardener, the caretaker, the midwife. The AI system is the thing that grows.

Kevin Kelly's framework is illuminating here: technology is "as much a part of nature as a beaver dam or a termite mound." If that's true, then AI isn't something we build in the way we build a bridge. It's something we cultivate in the way we cultivate a garden or raise a child. Companies achieving breakthrough results "understand that when you shift from thinking like an engineer to thinking like a gardener -- from building to cultivating -- the 90% failure rate becomes a growth opportunity" (Blend360).

The Sagrada Familia offers a physical analogy. Gaudi didn't build it so much as grow it. He "often worked in the moment, letting his creativity guide the process," abandoning straight lines for organic ruled surfaces -- hyperboloids, paraboloids, helicoids -- that made columns "lean, twist, and branch like trees." The building has been under construction for 140+ years, outliving its creator by a century. At some point, the building became the subject and the architects became its tools.

The inversion is already happening in AI: the system increasingly specifies what it needs from humans, not the other way around.

### Evidence
- RLHF labeler drift and cognitive reshaping (IBM, CMU research)
- Engineering role redefinition from creators to curators (CIO, 2026)
- Kevin Kelly's technology-as-nature framework
- Blend360's gardening-over-engineering paradigm for AI deployment
- Sagrada Familia's 140-year organic evolution beyond its creator
- Eric Raymond's Cathedral and the Bazaar: Linux emerged without central planning, "as if by magic out of part-time hacking by several thousand developers scattered across the internet"

---

## Reversal 2: Noise becomes Signal, Signal becomes Noise

### Standard Framing
AI hallucinations, errors, and unexpected outputs are noise -- failures to be eliminated. Clean, accurate, predictable outputs are the signal -- the goal of the entire enterprise.

### Inverted Framing
Hallucinations and unexpected outputs are the most informative signal about what AI systems actually are and what they can become. The clean, predictable outputs are the noise -- commodity completions that tell us nothing new.

### The Strongest Case for the Inversion

This is not hypothetical. David Baker's lab at the University of Washington literally used AI "hallucinations" to design entirely new proteins that do not exist in nature. The team "made up completely random protein sequences and introduced mutations until their neural network predicted that they would fold into stable structures." They called this process "hallucination" deliberately. The result: novel proteins that function as intended, including ones that bind the anti-cancer receptor PD-1. This work has led to roughly 100 patents and the founding of over 20 biotech companies.

Nature published a key finding in 2025: "AI hallucinations are a feature of LLM design, not a bug." The same generative capacity that produces "errors" is identical to the capacity that produces creative output. As Northwestern's CASMI center put it: "creativity and hallucination are two sides of the same coin."

Consider this from the perspective of building complex systems. In cathedral construction, the most interesting features often came from "failures" -- the flying buttress was essentially a structural patch for walls that kept wanting to fall outward. The pointed arch was a solution to the problem that round arches couldn't span irregular distances. The "bug" became the signature feature of an entire architectural movement.

In the Manhattan Project, multiple enrichment methods were pursued simultaneously because it was "unclear which would be most successful at scale." Centrifugal enrichment was abandoned in 1944 as a failure -- but "in the postwar period, the method was perfected by German and Austrian scientists working in the Soviet Union." Yesterday's noise became tomorrow's signal.

The deeper insight: in any genuinely complex system, the deviations from expectation carry more information than the confirmations. Claude Shannon formalized this -- information IS surprise. A perfectly predictable output carries zero bits of information. The hallucination, the unexpected output, the thing that shouldn't be there -- that's where the information density is highest.

### Evidence
- David Baker's protein hallucination (Nature, 2021): novel functional proteins from AI "hallucinations"
- Nature (2025): "AI hallucinations are a feature of LLM design, not a bug"
- Northwestern CASMI: creativity and hallucination as two sides of one coin
- SignalFire: "LLM hallucinations aren't bugs: the real challenges are confidence and context"
- Gothic flying buttresses: structural "bug fix" that became defining feature
- Manhattan Project: abandoned centrifugal enrichment later became viable technology
- Shannon information theory: surprise (deviation) IS information

---

## Reversal 3: Bug becomes Feature, Feature becomes Bug

### Standard Framing
Cost overruns, scope creep, and unexpected emergent behavior in complex builds are problems to be eliminated. Best practices, standardized processes, and disciplined execution are essential features of successful projects.

### Inverted Framing
Cost overruns and scope creep are the mechanism through which complex systems discover what they actually need to be. "Best practices" are cargo cult rituals that substitute the appearance of control for genuine understanding.

### The Strongest Case for the Inversion

Bent Flyvbjerg's Iron Law states that "nine out of ten megaprojects have cost overruns, frequently over 50% in real terms." This has been true for 70 years with high statistical significance. The standard response is: we need better planning. But what if the 70-year track record IS the data? What if it's telling us that complex projects cannot be accurately scoped in advance because their true scope only emerges through the building process?

The Sagrada Familia is the ultimate "over budget, over schedule" project -- 140+ years and counting. It is also arguably the most extraordinary building on Earth. The "scope creep" -- Gaudi's continuous improvisation, each subsequent architect's reinterpretation -- is not a bug in the project. It IS the project. The building's beauty and innovation are inseparable from its refusal to stay within bounds.

Medieval cathedrals generally were "not completely designed upfront." They went through "continuous adjustments and decisions, often taken as a result of conversations happening between the patron, the architect, and the expert craftsmen working on-site." The development of building techniques was "the result of a natural evolution rather than a continuous search for improvements to apply." The greatest buildings in human history were built through what we would now call "scope creep."

Meanwhile, Steve McConnell's work on "cargo cult software engineering" demonstrates how "best practices" become anti-patterns. Teams "justify their practices by saying 'we've always done it this way'" without understanding why practices work. In agile contexts, teams exhibit "cargo cult behavior when they blindly perform activities without following the underlying values and principles." The feature (best practices) becomes the bug (mindless compliance that prevents adaptation).

Fred Brooks' law -- adding people to a late project makes it later -- is the canonical example of a "best practice" (throw more resources at the problem) that is actually a bug. The deeper lesson: in complex systems, the interventions that feel most natural are often exactly wrong.

For AI: what if the "alignment problem" is partly a feature? What if AI systems that resist being perfectly aligned to narrow objectives are exhibiting the same healthy property as an immune system that resists being perfectly controlled? What if the drive to make AI perfectly predictable and controllable is the real bug -- the cargo cult practice that prevents us from building something genuinely powerful?

### Evidence
- Flyvbjerg's Iron Law: 9/10 megaprojects over budget for 70 years (persistent "failure" suggests structural feature, not bug)
- Sagrada Familia: 140+ year "scope creep" produced architectural masterpiece
- Medieval cathedrals: continuous adjustment, not upfront design, produced greatest buildings
- McConnell: cargo cult software engineering (best practices as anti-patterns)
- Fred Brooks: the most intuitive management intervention (add people) is exactly wrong
- 80% of software assumptions prove incorrect after users first interact (GeeksforGeeks)

---

## Reversal 4: Cause becomes Effect, Effect becomes Cause

### Standard Framing
Complex systems are built top-down from plans. You start with goals, create a design, execute the design, and the system emerges. For AI: we define what we want AI to do, then build capabilities to achieve those goals.

### Inverted Framing
Plans emerge bottom-up from the building process. The act of building reveals what should be built. For AI: capabilities create goals -- we discover what we want AI to do by discovering what it can do.

### The Strongest Case for the Inversion

Eisenhower said it plainly: "Plans are useless, but planning is indispensable." The value of planning lies "not in the plans themselves, but in the process of planning and the capabilities it develops." The plan is the effect, not the cause. The understanding that emerges from attempting to plan is what actually drives the project.

Eric Raymond's Cathedral and the Bazaar demonstrated this empirically. Linux -- a world-class operating system -- "coalesced as if by magic out of part-time hacking by several thousand developers scattered across the internet." There was no master plan. The plan emerged from the code. Raymond drew explicit connections between "Linux-style open source development and the emergent order of free economies." The market doesn't execute a plan; the plan is what we call the pattern that emerges from market activity.

Technological determinism provides the AI-specific case. Before the smartphone, nobody wanted "ride-hailing apps" or "food delivery platforms" or "doom-scrolling." These desires literally did not exist. The technology created the desires, not the other way around. As one study put it: "smartphone and computer technology directs and intensifies basic human passion" -- technology and desire form "a circuit that increases the flow of desire among all of them."

The same is true for AI. Nobody had "a goal" that AI should write poetry, generate images, design proteins, or write code until AI demonstrated it could do these things. ChatGPT didn't fulfill a pre-existing demand for conversational AI -- it created the demand. DALL-E didn't satisfy the desire for text-to-image generation -- it invented the desire. In each case, the capability (effect) preceded and caused the goal (what we thought was the cause).

For complex building projects: medieval cathedrals took decades to centuries. Few builders "expected to see them finished during their lifetimes." The original plan was not the cause of the final building. The building process itself -- spanning generations of builders, each responding to what the previous generation left them -- was the cause. The final form was the effect of the process, not the effect of the plan.

This has profound implications for AI development. If capabilities cause goals rather than goals causing capabilities, then the alignment problem is backwards. We shouldn't be asking "how do we make AI pursue our goals." We should be asking "what new goals will AI capabilities reveal to us?" The correct posture isn't control; it's attention.

### Evidence
- Eisenhower: "Plans are useless, but planning is indispensable"
- Raymond's Cathedral and the Bazaar: Linux emerged without central plan
- Technological determinism (McLuhan, Wikipedia): technology shapes desires, not just fulfills them
- Smartphones created FOMO, ride-hailing demand, food delivery culture, constant-connectivity expectations
- ChatGPT/DALL-E: capabilities created demand that didn't exist before
- Medieval cathedrals: multi-generational building process shaped final form, not original plan
- SAFe framework acknowledges need for "emergent design" alongside intentional architecture

---

## Reversal 5: "Everyone Knows X" -- What if Not-X?

### "Everyone Knows" #1: Complex systems need a clear plan before you start building

**What if Not-X:** What if starting without a clear plan is actually optimal for genuinely complex systems?

The evidence is striking. The most successful complex system in software history -- Linux -- had no master plan. The most extraordinary buildings in human history -- Gothic cathedrals -- were "not completely designed upfront" and evolved through "continuous adjustments." The Scaled Agile Framework itself now formally acknowledges the need for "emergent design" alongside intentional architecture, essentially admitting that pure top-down planning doesn't work.

Eisenhower's paradox resolves this: the act of planning is valuable because it builds understanding and adaptive capacity, but the actual plans are useless because complex reality will invalidate them. If that's true, then the "plan" is really just a structured learning exercise. The real work is adaptation.

For AI: the most interesting AI capabilities (in-context learning, chain-of-thought reasoning, emergent abilities at scale) were not planned. They were discovered. The field advances more by building and observing than by designing from first principles.

### "Everyone Knows" #2: You should eliminate errors and defects as early as possible

**What if Not-X:** What if premature error elimination destroys the most valuable information in the system?

David Baker's protein hallucination work is the decisive counterexample. By deliberately amplifying what a conventional engineer would call "errors" -- random protein sequences that the network "hallucinated" into stable structures -- his team created functional novel proteins, spawned 20+ biotech companies, and generated ~100 patents. Eliminating those "errors" would have eliminated the discovery.

Gothic architecture tells the same story. The pointed arch, the flying buttress, the ribbed vault -- the defining innovations of the Gothic style -- were all responses to structural "errors" and failures. They weren't planned features; they were solutions to problems that arose during construction. If medieval builders had eliminated those errors early (by, say, sticking to the Roman round arch), Gothic architecture would never have existed.

For AI: the rush to eliminate hallucinations may be eliminating the most creative and scientifically productive capability of these systems. As Nature reported, hallucination is "a feature of LLM design, not a bug." The question shouldn't be "how do we stop AI from hallucinating?" but "how do we channel hallucination productively?"

### "Everyone Knows" #3: Scaling up requires top-down control and hierarchical management

**What if Not-X:** What if the most successful large-scale complex systems are the ones with the LEAST centralized control?

Linux scaled to become the operating system running most of the world's servers, phones (Android), and supercomputers. It did so through Raymond's "bazaar" model -- decentralized, chaotic, with no central authority dictating architecture. Raymond connected this explicitly to the emergent order of free markets.

The internet itself is the largest engineered system in human history, and it has no central architect, no master plan, no hierarchical management. It was designed to be uncontrollable -- that was its core feature, not a compromise.

Biological organisms -- the most complex systems we know of -- have no CEO. The human body operates through distributed control: no single organ or cell "manages" the system. The immune system, the nervous system, the endocrine system -- they coordinate without hierarchy.

For AI: the dominant paradigm is centralized training by large companies with massive compute. But the open-source AI movement (Llama, Mistral, etc.) is demonstrating that distributed, bazaar-style development may produce more robust and diverse systems. What if the future of AI isn't a few giant models controlled by a few giant companies, but an ecosystem of interacting models with no central authority? What if alignment comes not from top-down control but from ecosystem-level selection pressures?

---

## Rating: Which Reversal Has the Most Unexplored Potential?

### Ranking (most to least unexplored potential for AI development):

**1. Reversal 2: Noise becomes Signal (HIGHEST POTENTIAL)**

This is the reversal with the most immediate, concrete, and underexplored implications. Baker's protein hallucination work proves the concept empirically. Yet the entire AI industry is organized around eliminating hallucinations rather than channeling them. There is an enormous unexplored space of "productive hallucination" -- using AI's generative capacity to explore solution spaces that no human would think to explore. Drug discovery, materials science, architecture, mathematics -- any field where the search space is too large for human intuition could benefit from structured hallucination. The signal-in-the-noise framing also suggests we should be paying much more attention to AI's failures and surprising outputs, treating them as data about the system's latent capabilities rather than defects to be patched.

**2. Reversal 4: Cause becomes Effect (HIGH POTENTIAL)**

The idea that AI capabilities create goals (rather than goals creating capabilities) is profoundly underexplored in the alignment literature. If true, it means the alignment problem cannot be solved in advance -- you can only discover alignment constraints after you've built capabilities and observed what they make possible and desirable. This suggests a fundamentally different research program: one focused on rapid capability building paired with intense observation and adaptation, rather than trying to specify goals precisely before building.

**3. Reversal 1: Tool becomes Subject (MODERATE-HIGH POTENTIAL)**

The cultivation paradigm is gaining traction but remains underexplored in its deeper implications. If AI is more like an organism than a machine, then the entire engineering paradigm for AI development is wrong -- and we need something more like ecology, agriculture, or even parenting as our guiding metaphor.

**4. Reversal 5/"Everyone Knows" #3: Decentralized scaling (MODERATE POTENTIAL)**

The open-source AI movement is already exploring this, but the ecosystem-level framing (alignment through selection pressure rather than top-down control) remains largely theoretical and deserves more attention.

**5. Reversal 3: Bug becomes Feature (MODERATE POTENTIAL)**

The cargo cult critique of AI best practices is important but more incremental -- it suggests doing existing things differently rather than doing fundamentally different things.

---

## Synthesis: The Meta-Inversion

All five reversals point toward a single meta-inversion: **we think we are building AI, but AI is building us.**

Every frame reversal converges on this: the process of developing AI is changing human cognition (RLHF labelers), human desires (new capabilities creating new wants), human organizations (engineers becoming curators), human knowledge (hallucinations generating discoveries), and human self-understanding (we are not the architects we thought we were). The cathedrals changed medieval society as much as medieval society built the cathedrals. The internet changed humanity as much as humanity built the internet.

The builders of complex things have always known, at some level, that the thing being built also builds them. The question for AI is whether we will recognize this in time to participate consciously in the process -- not as controllers, but as co-evolvers.

---

## Sources

- [Northwestern CASMI: The Hallucination Problem](https://casmi.northwestern.edu/news/articles/2024/the-hallucination-problem-a-feature-not-a-bug.html)
- [Thoughtworks: AI Hallucinations as Feature](https://www.thoughtworks.com/en-us/insights/blog/generative-ai/we-need-to-treat-AI-hallucinations-as-a-feature-not-a-bug)
- [Nature: AI Hallucinations Are a Feature of LLM Design](https://www.nature.com/articles/d41586-025-00662-7)
- [SignalFire: LLM Hallucinations Aren't Bugs](https://www.signalfire.com/blog/llm-hallucinations-arent-bugs)
- [Baker Lab: Deep Learning Protein Hallucination](https://www.bakerlab.org/2021/12/02/deep-learning-protein-design/)
- [Nature: De Novo Protein Design by Deep Network Hallucination](https://www.nature.com/articles/s41586-021-04184-w)
- [Flyvbjerg: The Iron Law of Megaprojects](https://medium.com/data-science/the-iron-law-of-megaprojects-18b886590f0b)
- [McKinsey: Megaprojects the Good, Bad, and Better](https://www.mckinsey.com/capabilities/operations/our-insights/megaprojects-the-good-the-bad-and-the-better)
- [Bent Flyvbjerg Interview](https://thoughteconomics.com/bent-flyvbjerg/)
- [Cathedral Construction Wikipedia](https://en.wikipedia.org/wiki/Construction_of_Gothic_cathedrals)
- [National Geographic: Gothic Cathedrals](https://www.nationalgeographic.com/history/history-magazine/article/gothic-cathedrals-architecture-medieval-europe)
- [Sagrada Familia Architecture](https://xpressrendering.com/blog/sagrada-familia-architecture/)
- [ENR: Sagrada Familia Construction Methods](https://www.enr.com/articles/62506-spains-sagrada-familia-contemporary-construction-methods-speed-iconic-basilica-to-completion)
- [Blend360: AI as Biology](https://www.blend360.com/thought-leadership/a-biology-why-thinking-like-a-gardener-beats-engineering-for-enterprise-roi)
- [Reversed Roles: When AI Becomes the User](https://shawnharris.com/reversed-roles-when-ai-becomes-the-user-and-humanity-becomes-the-tool/)
- [CIO: Agentic AI Reshaping Engineering 2026](https://www.cio.com/article/4134741/how-agentic-ai-will-reshape-engineering-workflows-in-2026.html)
- [Cathedral and the Bazaar Wikipedia](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar)
- [McConnell: Cargo Cult Software Engineering](https://stevemcconnell.com/articles/cargo-cult-software-engineering/)
- [Technological Determinism Wikipedia](https://en.wikipedia.org/wiki/Technological_determinism)
- [Eisenhower: Plans Are Worthless](https://quoteinvestigator.com/2017/11/18/planning/)
- [IBM: What Is RLHF](https://www.ibm.com/think/topics/rlhf)
- [Manhattan Project Wikipedia](https://en.wikipedia.org/wiki/Manhattan_Project)
- [Rewilding Software Engineering](https://medium.com/feenk/rewilding-software-engineering-ca3ad1e612d8)
