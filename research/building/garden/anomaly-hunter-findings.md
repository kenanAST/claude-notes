# Anomaly-Hunter Findings: What's WEIRD About Building Complex Things

## Anomaly #1: The Negative Learning Curve — Experience Makes You Worse

### The Anomaly
Nuclear reactor construction costs have *increased* with cumulative experience, the exact opposite of what learning curve theory predicts. In the US, construction costs more than doubled with each doubling of cumulative capacity (a learning rate of -115%). Even France — the gold standard of nuclear standardization, with centralized decision-making and identical reactor designs — saw substantial real-term cost escalation across its program.

This isn't a minor deviation. Every technology humanity has ever scaled — solar panels, semiconductors, automobiles, aircraft — shows positive learning curves where costs decrease 15-30% with each doubling of production. Nuclear power is the lone, glaring exception.

### Why It's Weird / What Framework It Violates
This violates the most fundamental law in manufacturing economics: Wright's Law / the experience curve. The entire premise of industrialization is that doing something repeatedly makes you better and cheaper at it. Nuclear construction doesn't just fail to follow this law — it *reverses* it. Even South Korea, which builds reactors every 3 years with the same organization designing, building, owning, and operating them ($3,571/kW vs US $5,833/kW vs France $7,931/kW), only manages to hold costs roughly flat rather than achieving the steep declines seen in other technologies.

The deeper anomaly: safety knowledge and operational experience actually *generate* complexity. Every accident, near-miss, and discovered failure mode adds new requirements, new regulations, new systems. The system learns about its own dangers and must become more complex to address them. Learning makes the thing harder.

### What It Might Mean for AI Development
AI systems may face an analogous negative learning curve as they scale. Every discovered failure mode (hallucinations, jailbreaks, alignment failures, emergent dangerous capabilities) adds new safety requirements, RLHF layers, guardrails, monitoring systems, and evaluation suites. The cost of making AI "safe enough" may increase faster than the cost of making it "capable enough" decreases. We may already be seeing this: the cost of frontier model training has increased by orders of magnitude, and a significant and growing fraction of that cost is safety-related.

The South Korea exception is also instructive: the one country that avoided the worst of the negative learning curve did so through *vertical integration* and *continuous production cadence* — the same org designs, builds, operates, and owns. In AI, this suggests that organizations which tightly integrate research, training, deployment, and safety (rather than fragmenting these across different teams or even different companies) may avoid the worst cost escalation.

### Sources
- [The costs of the French nuclear scale-up: A case of negative learning by doing](https://www.sciencedirect.com/science/article/abs/pii/S0301421510003526) (Grubler, 2010, Energy Policy)
- [Why Does Nuclear Power Plant Construction Cost So Much?](https://ifp.org/nuclear-power-plant-construction-costs/)
- [Sources of Cost Overrun in Nuclear Power Plant Construction](https://www.cell.com/joule/fulltext/S2542-4351(20)30458-X) (Joule, 2020)
- [How to Build Low-Cost Nuclear: Lessons from the world](https://www.cis.org.au/publication/how-to-build-low-cost-nuclear-lessons-from-the-world/)
- [What's Holding Back Nuclear in the West?](https://www.bcg.com/publications/2025/whats-holding-back-nuclear-in-the-west) (BCG, 2025)

---

## Anomaly #2: Tacit Knowledge Is the Actual Product — And It Can't Be Written Down

### The Anomaly
TSMC's Arizona fab uses the exact same ASML machines, the same process recipes, and the same documented procedures as TSMC's fabs in Taiwan. Yet wafers cost 30-50% more and yields are slower to improve. TSMC's response was not to send more documentation — it was to physically relocate hundreds of experienced workers from Taiwan to Arizona.

Similarly, the United States discovered it could no longer manufacture a critical nuclear warhead component because the engineers who knew how had retired. It cost $69 million and five years to re-learn what a handful of people once knew. NASA's Saturn V blueprints still exist, but the practical knowledge of how to build the rocket scattered with the team — the blueprints alone are useless. Plant Vogtle, America's first new nuclear reactor in decades, came in $21 billion over budget and 7 years late, largely because the construction workforce had no institutional memory of how to build one.

Research estimates that 70% of critical operational knowledge in manufacturing is "tribal" — never written down, never formally taught.

### Why It's Weird / What Framework It Violates
This violates the Enlightenment assumption that underpins all of modern engineering: that knowledge can be made explicit, documented, and transferred through specifications. The entire paradigm of engineering — blueprints, specifications, standards, procedures — assumes that if you write down the right instructions, anyone can follow them. The TSMC case proves this is false for the most advanced manufacturing on Earth. The knowledge that matters most literally cannot be documented. It exists in the bodies and habits of experienced workers.

This also violates the standard model of technology transfer. You can't just buy the machines and read the manuals. The "recipe" isn't the recipe — the cooks are.

### What It Might Mean for AI Development
This has profound implications for AI. If building complex things depends on undocumentable tacit knowledge, then:

1. **AI training may carry irreproducible tacit knowledge.** The specific sequence of hyperparameter tuning decisions, data curation choices, and training run interventions made by experienced ML engineers may constitute tacit knowledge that cannot be fully captured in papers or codebases. This could explain why reproducing published results is notoriously difficult.

2. **AI safety expertise may be inherently non-transferable.** If the knowledge of how to align and control AI systems is partially tacit, it cannot simply be published and adopted by other labs. The safety knowledge lives in the people, not the documents.

3. **The "open source vs. closed" debate misses the point.** Even fully open weights and code may not transfer the actual capability, because the tacit knowledge of how to use them effectively stays with the originating team.

4. **Paradoxically, AI itself might be the first technology that can *capture* tacit knowledge** — by learning patterns that humans can sense but cannot articulate. This could be transformative for manufacturing and construction if AI can encode the "feel" that experienced workers have.

### Sources
- [Tacit Knowledge Transfer Makes the News](https://developsense.com/blog/2023/10/tacit-knowledge-transfer-makes-the-news)
- [In a knowledge economy, the supply chains that matter are in your head](https://richardvigilante.substack.com/p/in-a-knowledge-economy-the-supply)
- [Culture Clash in TSMC's Phoenix Fab](https://www.chinatalk.media/p/culture-clash-in-tsmcs-phoenix-fab)
- [The Advanced Semiconductor Supply Chain: Why Money Is Not Enough](https://medium.com/@marc.bara.iniesta/the-advanced-semiconductor-supply-chain-why-money-is-not-enough-e39325015d01)
- [The Tribal Knowledge Crisis in Manufacturing](https://manual.to/the-tribal-knowledge-crisis-in-manufacturing/)

---

## Anomaly #3: The Survival of the Unfittest — The Worst Projects Get Built

### The Anomaly
Bent Flyvbjerg's research across thousands of megaprojects reveals a devastating pattern: 9 out of 10 megaprojects exceed their budgets, with overruns of 50%+ being common (Channel Tunnel: 80%, Denver Airport: 200%, Boston Big Dig: 220%). But here's the truly anomalous part: this isn't random failure. It's *systematically selected for*.

Flyvbjerg identifies what he calls "the survival of the unfittest" — because projects are approved based on projected costs and benefits, and because planners systematically underestimate costs and overestimate benefits, the projects that get built are not the best projects but the ones with the most distorted projections. The more a project's numbers lie, the more likely it is to be approved. Decades of data showing this pattern have not changed it.

Albert Hirschman proposed the opposite interpretation: the "Hiding Hand" principle, which suggests projects succeed *because* planners underestimate difficulty — if they knew the true cost, they'd never start, but once committed, human creativity solves problems. However, rigorous statistical testing rejects this principle at p < 0.0001.

### Why It's Weird / What Framework It Violates
This violates rational choice theory and the entire premise of cost-benefit analysis. In any rational system, better information should lead to better decisions. But megaproject planning actively resists better information because the incentive structure rewards deception: planners who give honest estimates don't get their projects approved. This creates an anti-learning system where the feedback loop is broken — failure doesn't lead to correction because the people who made the estimates have moved on by the time costs are known.

The deeper anomaly is that despite Flyvbjerg publishing this research widely and it being well-known, nothing has changed. Knowing about the bias does not fix it. This suggests the bias isn't cognitive — it's structural and incentive-driven.

### What It Might Mean for AI Development
The AI industry may be in a "survival of the unfittest" dynamic right now. The AI projects that attract the most funding and attention may be the ones with the most optimistic projections about timelines, capabilities, and safety. Labs that give conservative estimates about when they'll achieve AGI or how much alignment work is needed may be outcompeted by labs with more aggressive (and potentially more distorted) projections.

This also applies to AI safety: the "cost" of safety measures is systematically underestimated in project planning, just as environmental and safety costs are in physical megaprojects. Safety work that honestly accounts for the difficulty of alignment may lose funding to work that minimizes the challenge.

The Hirschman counterargument — that ignorance of difficulty enables innovation — has a kernel of truth in AI: many of AI's greatest advances came from teams that didn't know how hard the problem was supposed to be. But the statistical rejection of the Hiding Hand suggests this is survivorship bias, not a reliable strategy.

### Sources
- [Introduction: The Iron Law of Megaproject Management](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2742088) (Flyvbjerg)
- [The Iron Law of Megaprojects](https://medium.com/data-science/the-iron-law-of-megaprojects-18b886590f0b)
- [The Principle of the Malevolent Hiding Hand](https://arxiv.org/pdf/1509.01526)
- [The Fallacy of Beneficial Ignorance: A Test of Hirschman's Hiding Hand](https://www.sciencedirect.com/science/article/abs/pii/S0305750X15301030)
- [Why Megaprojects Systemically Fail](https://www.sbs.ox.ac.uk/oxford-answers/why-megaprojects-systemically-fail-and-what-can-be-done-about-it)

---

## Anomaly #4: Cathedrals Succeeded by Being Permanently Unfinished — The Anti-Specification

### The Anomaly
Medieval cathedrals — among the most complex structures ever built — were constructed over 50-600 years, across multiple generations, without complete blueprints, without a fixed endpoint, and often without a single architect overseeing the whole. Yet they achieved extraordinary structural sophistication. The nave of Laon Cathedral (begun 1175) reached 80 feet; Rheims (begun just 50 years later) soared to 125 feet. Quality *improved* across the centuries-long build.

The key insight: an unfinished cathedral is not a failure. A single room could function as a cathedral. Services commenced almost immediately in temporary wooden chapels while stone construction continued for decades. The design was modular down to individual stones, robust against uncertainties and interruptions. There was no "launch date" — value was delivered continuously from day one.

This is the exact opposite of how modern megaprojects work, where nothing works until everything works (a nuclear reactor at 95% completion produces zero electricity).

### Why It's Weird / What Framework It Violates
This violates the modern project management paradigm entirely: fixed scope, fixed timeline, fixed budget, defined requirements, waterfall execution. Cathedrals had none of these. They violated every principle in the PMBOK. Yet they produced structures that have lasted 800+ years.

The deeper anomaly: the cathedral builders had sophisticated engineering knowledge — understanding of force vectors, use of iron reinforcement (proven at Beauvais Cathedral dating to 1225), geometric proportional systems — but transmitted this knowledge orally and through practice rather than through documentation. They combined advanced technical capability with pre-modern knowledge management, and it worked better than our documented, credentialed, certified approaches.

The SpaceX parallel makes this even more anomalous: SpaceX's Starship ($3B/5 years) vs NASA SLS ($23B/13 years) suggests that the cathedral model — iterate rapidly, fail fast, deliver value incrementally, don't over-specify — works better in the 21st century too. The "modern" approach (waterfall, extensive documentation, risk-averse planning) consistently underperforms the "medieval" approach (iterate, adapt, deliver continuous value).

### What It Might Mean for AI Development
This suggests the right model for building AI systems is not the waterfall/megaproject model (define requirements, design architecture, build to spec, test, deploy) but the cathedral model:

1. **Start delivering value immediately** with simple systems, and evolve complexity over time (consistent with Gall's Law: "A complex system that works evolved from a simple system that worked").
2. **Design for modularity** so that partial completion is still valuable and components can be improved independently.
3. **Embrace multi-generational construction** — accept that building safe, aligned AGI may take decades of iterative work across many teams, rather than a single moonshot project.
4. **Transmit knowledge through practice, not just papers** — apprenticeship and hands-on collaboration may be more effective than documentation for the tacit knowledge problem (see Anomaly #2).

The SpaceX evidence strengthens this: rapid iteration with tolerance for failure outperforms careful planning. This is exactly the debate happening in AI safety between "move fast and iterate" vs. "get it right before deploying."

### Sources
- [The Cathedral and the Starship: Learning from the Middle Ages for Future Long-Duration Projects](https://www.centauri-dreams.org/2020/07/17/the-cathedral-and-the-starship-learning-from-the-middle-ages-for-future-long-duration-projects/)
- [Building a Cathedral](https://www.scopeofwork.net/building-a-cathedral/)
- [The Construction of Gothic Cathedrals](https://misfitsarchitecture.com/2024/03/03/the-construction-of-gothic-cathedrals/)
- [Behind The Product: NASA SLS vs SpaceX Starship](https://productside.com/behind-the-product-nasa-sls-vs-spacex-starship/)
- [How Complex Systems Fail](https://how.complexsystems.fail/)

---

## Anomaly #5: Emergence in Complex Builds — The System Becomes Smarter Than Its Builders

### The Anomaly
Two radically different domains show the same strange pattern: capabilities emerge from complex systems that no designer intended or predicted.

In biology, embryonic development is a guided self-organizing process where tissues organize independently of external signals. No cell "knows" the blueprint for the whole organism. Alan Turing's morphogen theory (1952) showed that simple chemical reactions plus diffusion can generate complex patterns — stripes, spots, branching structures — that aren't encoded anywhere in the system. The "blueprint" (DNA) doesn't specify the organism; it specifies local rules whose interaction produces emergent global structure.

In AI, large language models exhibit emergent capabilities — multi-step arithmetic, question-answering, emoji-based movie identification — that appear sharply at critical scales with no gradual improvement beforehand. Researchers compiled lists of dozens of emergent behaviors and that list continues to grow. These capabilities were not designed or intended by the builders; they arose from scale alone.

In software, Richard Gabriel's "Worse is Better" principle showed that simpler, cruder systems (Unix, C) beat more elegant, carefully-designed systems (Lisp machines, CORBA) because simplicity enabled viral adoption and evolutionary improvement. The system that won was not designed to be the best — it was designed to be simple enough to survive and evolve.

### Why It's Weird / What Framework It Violates
This violates the engineering paradigm that says you get out what you design in. In standard engineering, a bridge does exactly what the blueprint specifies — no more, no less. But in complex adaptive systems (biological, software, AI), the artifact can develop capabilities that were never specified, never intended, and sometimes not even understood by its creators.

This is deeply anomalous because it means the most important properties of the most complex things we build are not designed — they emerge. The builders of GPT-4 did not design its ability to pass the bar exam. Evolution did not design human consciousness. The cathedral builders did not design the acoustic properties of Gothic naves that make them perfect for choral music. These properties *emerged* from the interaction of simpler design choices.

### What It Might Mean for AI Development
This is perhaps the most consequential anomaly for AI. If the most important capabilities of complex systems emerge rather than being designed:

1. **AI alignment cannot be fully "designed in."** Just as you can't predict emergent capabilities, you can't predict emergent misalignment. Safety must be treated as an ongoing, adaptive process (like the cathedral model), not a one-time design specification.

2. **The "scaling is all you need" intuition has a deeper basis than most realize.** Scaling laws show that simple power-law relationships govern AI performance across seven orders of magnitude. This is the AI equivalent of Turing's morphogens: simple rules at scale produce qualitatively new phenomena. The unreasonable effectiveness of scaling may be a manifestation of the same principles that make embryogenesis work.

3. **The "Worse is Better" principle applies to AI architectures.** The transformer architecture is not the theoretically optimal architecture for intelligence — it's the one that was simple enough to scale. Just as Unix beat Lisp machines, transformers beat more elegant approaches because they were simple enough to train at massive scale and robust enough to exhibit emergent capabilities.

4. **We should expect continued surprises.** The history of complex builds shows that emergence is the rule, not the exception, for systems above a certain complexity threshold. The most important capabilities (and risks) of future AI systems will likely be ones we haven't anticipated.

### Sources
- [The Unpredictable Abilities Emerging From Large AI Models](https://www.quantamagazine.org/the-unpredictable-abilities-emerging-from-large-ai-models-20230316/) (Quanta Magazine)
- [Emergent Abilities in Large Language Models: A Survey](https://arxiv.org/html/2503.05788v2)
- [Principles of Self-Organization of the Mammalian Embryo](https://pmc.ncbi.nlm.nih.gov/articles/PMC8212876/)
- [Worse is Better](https://www.dreamsongs.com/WorseIsBetter.html) (Richard Gabriel)
- [Emergent Abilities in Large Language Models: An Explainer](https://cset.georgetown.edu/article/emergent-abilities-in-large-language-models-an-explainer/) (CSET Georgetown)

---

## Cross-Cutting Theme: The Five Anomalies Tell a Unified Story

These five anomalies aren't independent. They form a coherent — and disturbing — picture:

1. **Experience increases cost** (Anomaly #1) because learning reveals complexity rather than simplifying it.
2. **The critical knowledge can't be written down** (Anomaly #2) because the most important parts of building complex things are tacit and embodied.
3. **The selection process is broken** (Anomaly #3) because incentives reward optimism over accuracy, so the worst projects get built.
4. **The successful model is the opposite of what we teach** (Anomaly #4) because iterative, modular, continuously-valuable construction beats big-bang planning.
5. **The most important capabilities aren't designed** (Anomaly #5) because complex systems generate emergent properties their builders didn't intend.

The unified lesson for AI: **we are building something whose complexity will increase our costs over time, whose essential knowledge lives in people not documents, whose funding is driven by distorted projections, whose optimal construction method is the one we're least comfortable with (continuous iteration with tolerance for failure), and whose most important properties — both capabilities and dangers — will emerge unpredictably.**

Current AI development frameworks are not prepared for any of this.
