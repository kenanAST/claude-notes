# First-Principles Axiom Audit: Building Hard and Complex Things -- Lessons for AI

## Step 1: The Top 5 Foundational Assumptions Governing How We Build AI Systems

These assumptions are drawn not just from AI practice but from humanity's broader experience building complex systems (cathedrals, spacecraft, semiconductor fabs, biological organisms, large software systems).

### Assumption 1: Learning Requires Gradient-Based Optimization Over Differentiable Structures

The near-universal assumption that training an AI system means defining a differentiable loss function and using backpropagation with gradient descent to minimize it. This maps to the broader engineering assumption that *optimization requires continuous feedback through a well-defined objective function*. In cathedral building, this was the assumption that you needed a master builder with a complete plan; in spacecraft, that you needed exhaustive simulation before flight.

### Assumption 2: Intelligence Scales With Parameter Count and Data Volume

The "scaling hypothesis" -- that making models larger and training them on more data reliably produces more capable systems. This mirrors the engineering assumption that *capability scales with size and resources*: bigger reactors produce more power, taller buildings hold more people, more transistors enable faster computation.

### Assumption 3: Training and Inference Are Fundamentally Separate Phases

AI systems are built in two discrete phases: a massive offline training phase where the model learns, followed by a deployment/inference phase where the model is frozen and serves predictions. This mirrors the construction industry's separation between *design/build* and *occupancy/operation* -- you build the cathedral, then people use it. The building doesn't learn.

### Assumption 4: Intelligence Emerges From a Single Monolithic Architecture

The dominant paradigm is a single large model (typically a Transformer) that handles everything -- perception, reasoning, memory, generation -- within one unified architecture. This mirrors the *cathedral model* of building: one grand, integrated structure designed as a coherent whole, rather than a city that emerges from many independent structures.

### Assumption 5: Centralized Training on Centralized Compute Is Required

The assumption that building a frontier AI system requires concentrating enormous compute (thousands of GPUs) in one location, running massive synchronized training jobs for weeks or months. This mirrors the assumption in physical construction that *complex things require centralized coordination* -- a single general contractor, a single factory floor, a single mission control.

---

## Step 2: Classification -- LAW or CONVENTION?

### Assumption 1: Gradient-Based Optimization -- CONVENTION

**Classification: CONVENTION**

**What the actual law is:** To learn from data, a system needs *some* method of credit assignment -- determining which parameters or structures contributed to good or bad outcomes (information-theoretic necessity). The system must also navigate a search space to find good configurations (optimization). These are genuine requirements.

**Why gradient descent is a convention, not a law:**
- Biological brains do not use backpropagation. There is no known mechanism in the brain that propagates exact error gradients backward through layers of neurons. Yet brains learn extraordinarily well. The brain uses ~20 watts and learns from far fewer examples.
- Evolution itself is a powerful optimization algorithm that uses no gradients at all -- it operates through random variation and selection.
- Recent research (2025-2026) has produced viable alternatives: Forward-Forward algorithms, evolutionary strategies for training biophysical neural networks, liquid neural networks (Liquid AI achieved competitive performance with 90% smaller cache than Transformers), and perturbation-based methods like LOCO that provide unbiased gradient estimates without backpropagation.
- The convention persists because GPUs are optimized for matrix multiplication and backprop, creating a hardware-software co-dependency. The tool shapes the method.

**Historical parallel:** Before powered flight, engineers assumed you needed lighter-than-air gas (balloons) to fly. Heavier-than-air flight seemed to violate intuition. The Wright Brothers didn't violate any law of physics -- they broke a convention about *how* to achieve lift.

### Assumption 2: Intelligence Scales With Size -- PARTIAL LAW, MOSTLY CONVENTION

**The law part:** Information theory establishes that a system's capacity to model complex distributions is bounded by its representational capacity (related to parameter count) and the amount of information it has been exposed to (related to data volume). You cannot fit a 1TB model's worth of knowledge into 1KB of parameters. This is a genuine information-theoretic constraint.

**The convention part:** The *specific functional form* of scaling laws (loss ~ C/N^alpha) is empirical, not derived from first principles. As of early 2026, scaling laws are increasingly recognized as "a family of empirical regularities that hold only under specific regimes" rather than universal laws. Key evidence:
- The brain has ~86 billion neurons but uses ~20 watts. Current AI uses billions of times more energy per operation than the Landauer limit (kT ln 2 per bit erasure). This gap suggests massive inefficiency in current architectures, not that current scaling is the only path.
- Diminishing returns are appearing. The 2023-2025 literature shows that "emergent abilities" may be artifacts of evaluation design, not fundamental phase transitions.
- Data scarcity is becoming a binding constraint, challenging the assumption that you can always scale data.

**Historical parallel:** In semiconductor fabs, Moore's Law (transistor density doubles every ~2 years) was treated as a law for decades. It is actually a convention -- an empirical regularity that held under specific technological conditions. When those conditions changed (approaching atomic scales), the "law" broke down and required entirely new approaches (3D stacking, new materials, chiplets).

### Assumption 3: Training and Inference Are Separate -- CONVENTION

**Classification: CONVENTION**

**What the actual law is:** There is a genuine thermodynamic and information-theoretic cost to learning -- updating a model's internal state requires energy and computation. But nothing mandates that this must happen in a single offline batch before deployment.

**Why it's a convention:**
- Biological organisms learn continuously. There is no "training phase" for a human brain followed by a "deployment phase." Learning and acting are interleaved throughout life. The brain constantly updates its synaptic weights during inference (experience).
- Online learning, continual learning, and meta-learning already exist as research fields, demonstrating that the separation is not fundamental.
- The convention exists because of engineering convenience: batch training is easier to parallelize, debug, and reproduce. Separate phases simplify the engineering problem, just as separating design and construction simplifies building a skyscraper.

**Historical parallel:** SpaceX broke the convention of separating design and testing phases. Traditional aerospace (Boeing) used a waterfall approach: years of design, then build, then test. SpaceX adopted rapid iteration -- "build, test, learn, repeat" -- compressing 15+ year development cycles into 5 years and reducing launch costs by 66%. The phases were a convention, not a law.

### Assumption 4: Single Monolithic Architecture -- CONVENTION

**Classification: CONVENTION**

**What the actual law is:** A system that performs intelligent behavior needs *some* mechanism for: (a) representing information, (b) transforming information, (c) storing and retrieving information, and (d) making decisions. These functional requirements are genuine. But nothing dictates they must live in one architecture.

**Why it's a convention:**
- The brain is not a monolithic architecture. It consists of highly specialized subsystems (hippocampus for memory, visual cortex for perception, prefrontal cortex for planning, cerebellum for motor control) that evolved at different times and communicate through multiple mechanisms.
- Cities -- among humanity's most complex creations -- are not designed as monolithic structures. They emerge from many independent buildings, systems, and institutions that interact through shared infrastructure (roads, utilities, laws).
- The Transformer's dominance is partly a historical accident: the architecture happened to be well-suited to GPU parallelism and scaled well on available benchmarks. But as of 2025-2026, alternatives like State Space Models (Mamba), liquid neural networks, and hybrid architectures are achieving parity or superiority on key benchmarks. xLSTM achieves 3.5x faster training than equivalent Transformers.

**Historical parallel:** Early computers were monolithic -- a single CPU handled everything. The shift to heterogeneous computing (CPUs + GPUs + TPUs + specialized accelerators) unlocked orders-of-magnitude improvements. The monolith was a convention, not a law.

### Assumption 5: Centralized Training on Centralized Compute -- CONVENTION

**Classification: CONVENTION**

**What the actual law is:** There are genuine communication costs in distributed systems (latency, bandwidth limitations). Synchronizing gradients across many nodes introduces overhead. The speed of light imposes a hard floor on communication latency. These are laws.

**But centralization itself is a convention:**
- The internet itself is the counterexample: the most complex information system ever built is radically decentralized.
- Biological intelligence evolved in a massively distributed fashion -- no central server coordinated the evolution of billions of organisms.
- Federated learning, model merging, mixture-of-experts, and decentralized training protocols already demonstrate that centralization is not required.
- The convention persists because of economics (it's currently cheaper to buy one large cluster than coordinate many small ones) and because current training algorithms (synchronous SGD) were designed for centralized settings.

**Historical parallel:** Cathedral construction required centralized coordination under a master builder. But the most complex human artifact -- *civilization itself* -- emerged from massively decentralized, loosely coordinated activity over millennia. The cathedral model is one approach, not the only approach.

---

## Step 3: Drop All Conventions -- What Laws Remain?

After stripping away conventions, only these genuine constraints remain:

### LAW 1: Information-Theoretic Bounds on Representation
A system's ability to model a distribution is bounded by its representational capacity. You cannot losslessly compress more information than the entropy of the source allows (Shannon's source coding theorem). A model with N bits of storage cannot perfectly represent a distribution requiring >N bits to specify.

### LAW 2: Computational Irreducibility for Some Problems
Some computations cannot be shortcut -- you must run them to get the answer (Wolfram's computational irreducibility, related to Kolmogorov complexity). Not every intelligent behavior can be achieved by a lookup table; some require genuine computation.

### LAW 3: Thermodynamic Cost of Computation
Every irreversible bit operation dissipates at least kT ln 2 energy (Landauer's principle). Current computers operate ~1 billion times above this limit, but the limit exists and is inviolable. Any physically realized intelligence has energy costs.

### LAW 4: Credit Assignment Is Necessary for Learning
To improve from experience, a system must have some mechanism for determining which internal changes led to better outcomes. This is an information-theoretic necessity. The *specific mechanism* (backprop, evolution, Hebbian learning, etc.) is a convention, but the *need* for credit assignment is a law.

### LAW 5: No Universal Optimizer (No Free Lunch)
No single learning algorithm is optimal across all possible problems (Wolpert & Macready, 1997). Any system that performs well on a class of problems must embed assumptions (inductive biases) about that class. Intelligence requires *some* prior structure -- pure tabula rasa learning is impossible in finite time.

### LAW 6: Communication Costs in Distributed Systems
Information transfer between physically separated components is bounded by the speed of light and channel capacity (Shannon's channel coding theorem). Coordination has irreducible costs.

---

## Step 4: Clean-Sheet Design -- Rebuilding From Only the Laws

Given ONLY the six laws above, current technological capabilities (2026-era compute, data, algorithms), and NO knowledge of how AI is currently built, what would I design?

### Design Principle 1: Heterogeneous, Modular Architecture (From Laws 1, 5)

Since no single architecture is optimal for all problems (Law 5), and representational capacity bounds what a system can model (Law 1), a clean-sheet design would NOT be a single monolithic model. Instead:

- **A diverse ecosystem of specialized modules**, each optimized for different problem types. Some modules might be excellent at spatial reasoning, others at language, others at temporal prediction -- much like the brain's specialized regions.
- **Modules would use different computational substrates and learning algorithms.** Some might be differentiable, others might use evolutionary search, others might use symbolic reasoning. Forcing everything through one paradigm wastes the insight that different problems have different optimal algorithms.
- **A lightweight coordination layer** manages communication between modules, routing problems to the most appropriate specialist. This layer is the only thing that needs to be "general."

### Design Principle 2: Continuous Learning With Thermodynamic Awareness (From Laws 3, 4)

Since learning requires credit assignment (Law 4) but the specific mechanism is unconstrained, and computation has energy costs (Law 3):

- **The system learns continuously during operation**, not in a separate training phase. Every interaction provides learning signal. This is thermodynamically efficient because it amortizes the cost of learning over useful work, rather than paying a massive upfront energy cost for batch training.
- **Learning algorithms would be selected for energy efficiency**, not just convergence speed. Current backpropagation through massive networks is ~10^9 times above the Landauer limit. A clean-sheet design would prioritize local learning rules (Hebbian-like, forward-only) that minimize the energy cost per bit of knowledge acquired.
- **The system would have an explicit energy budget**, trading off exploration (learning new things) vs. exploitation (using what it knows) based on thermodynamic costs. Biological systems do this naturally; artificial ones should too.

### Design Principle 3: Hierarchical Compression With Computational Depth (From Laws 1, 2)

Since representation is bounded (Law 1) but some problems require irreducible computation (Law 2):

- **The system would build increasingly compressed representations at multiple levels of abstraction**, like the visual cortex's hierarchy from edges to shapes to objects to scenes.
- **For problems requiring genuine computation, the system would allocate variable compute** -- spending more "thinking time" on harder problems rather than applying the same fixed computation to every input (analogous to how humans spend more time on harder problems).
- **Memory would be separated from computation**: a massive, efficient long-term memory (cheap storage) combined with a smaller, expensive active computation space. Current LLMs embed everything in weights, which is like building a library where every book is carved into the walls.

### Design Principle 4: Distributed, Asynchronous Architecture (From Law 6)

Since communication has irreducible costs (Law 6), rather than fighting this with massive synchronization:

- **Modules would operate asynchronously**, communicating through shared representations rather than synchronized gradient updates. Each module learns and improves at its own pace.
- **Knowledge would be distributed**, with redundancy for fault tolerance. No single point of failure. Like a city's power grid, not a cathedral's single nave.
- **New modules could be added or removed without retraining the whole system.** This is how the internet works -- you add a server, it joins the network. You don't retrain the internet.

### Design Principle 5: Multi-Scale Optimization (From Laws 4, 5)

Since credit assignment is necessary but no single optimizer is universal:

- **Multiple optimization processes operating at different timescales**: fast adaptation (seconds, like attention), medium-term learning (hours, like weight updates), slow structural evolution (days-weeks, like architecture search).
- **The system would evolve its own learning algorithms**, using a meta-learning loop. The inner loop solves problems; the outer loop improves how the inner loop solves problems. This mirrors biological evolution (slow) producing organisms that can learn (fast).
- **Exploration would be first-class**, not just a regularization trick. The system would maintain explicit uncertainty estimates, seek out novel inputs, and allocate resources to reduce uncertainty where it matters most.

---

## Step 5: Comparing Clean-Sheet Design to Reality -- Innovation Gaps

### Gap 1: Monolith vs. Heterogeneous Ecosystem

| Aspect | Current Reality | Clean-Sheet Design |
|--------|-----------------|-------------------|
| Architecture | Single Transformer model does everything | Diverse ecosystem of specialized modules |
| Learning algorithm | Backpropagation everywhere | Different algorithms for different modules |
| Adding capability | Retrain the whole model | Add a new module |

**What the convention is:** "One model to rule them all" -- a single architecture, trained end-to-end, that handles all modalities and tasks.

**Why it persists:**
- End-to-end training is elegant and simple to implement.
- The Transformer architecture happened to scale well on GPUs.
- Benchmark culture rewards single-model performance.
- Venture capital and corporate incentives favor a single "product" (one model) over a complex ecosystem.

**What breaking it would look like:** A system with 10-50 specialized modules -- perhaps some Transformer-based, some SSM-based, some symbolic, some neuromorphic -- coordinated by a lightweight router that learns which module to invoke for which sub-problem. Modules would be independently trainable and replaceable. Like microservices replaced monoliths in software engineering.

**Evidence it could be broken:**
- Mixture-of-Experts models (like Switch Transformer, Mixtral) already move in this direction, activating different "experts" for different inputs.
- Liquid neural networks (Liquid AI, 2026) achieve competitive performance with radically different architectures and 90% smaller cache.
- State Space Models achieve parity with Transformers on many benchmarks, proving the architecture is not load-bearing.
- The brain itself is the existence proof: it uses different architectures for different functions.

### Gap 2: Batch Training vs. Continuous Learning

| Aspect | Current Reality | Clean-Sheet Design |
|--------|-----------------|-------------------|
| When learning happens | Massive offline training phase | Continuously, during operation |
| Adaptation speed | Weeks to months to update | Real-time |
| Energy profile | Enormous upfront cost, cheap inference | Moderate cost spread over lifetime |

**What the convention is:** Train once (for millions of dollars), deploy frozen, occasionally fine-tune.

**Why it persists:**
- Batch training is deterministic and reproducible -- important for safety testing and evaluation.
- Catastrophic forgetting remains an unsolved problem: continuous learning tends to overwrite old knowledge.
- Business models are built around the training-deployment split (train expensively, serve cheaply).
- Regulatory and safety frameworks assume a fixed, testable artifact.

**What breaking it would look like:** An AI system that genuinely improves from every interaction, accumulating knowledge without forgetting, adapting to new domains without retraining from scratch. Energy costs would be amortized over the system's lifetime rather than concentrated in a training run.

**Evidence it could be broken:**
- SpaceX proved that "design-then-build" is a convention, not a law. Their iterative approach (build-test-learn-repeat) compressed 15+ year timelines into 5 years and reduced costs by 66%. The same principle could apply to AI: learn while doing, not before doing.
- Online learning algorithms exist and work for specific settings.
- The brain never stops learning. Memory consolidation during sleep is a form of continuous learning that avoids catastrophic forgetting through interleaved replay.
- Retrieval-augmented generation (RAG) is a partial workaround, bolting external memory onto a frozen model. A clean-sheet design would integrate memory natively.

### Gap 3: Uniform Computation vs. Variable Compute Allocation

| Aspect | Current Reality | Clean-Sheet Design |
|--------|-----------------|-------------------|
| Compute per input | Fixed (same FLOPs for every token) | Variable (proportional to difficulty) |
| "Thinking time" | Determined by architecture | Determined by problem complexity |

**What the convention is:** Every input receives the same amount of computation (same number of layers, same attention operations), regardless of difficulty.

**Why it persists:**
- Fixed computation is easy to parallelize on GPUs.
- Variable computation breaks the neat batch-processing paradigm.
- Hardware is optimized for regular, predictable compute patterns.

**What breaking it would look like:** A system that detects difficulty in real-time and allocates more computation to harder problems -- "thinking longer" about complex questions and answering simple ones instantly. Some compute would be speculative, exploring multiple solution paths in parallel.

**Evidence it could be broken:**
- Chain-of-thought prompting and "reasoning models" (o1, o3) already implement a crude version of this: generating more tokens (more compute) for harder problems.
- Early-exit architectures allow tokens to "leave" the model at different layers.
- Mixture-of-Experts activates different amounts of computation per token.
- The human brain clearly allocates variable compute: you solve 2+2 in milliseconds but spend minutes on a complex proof.

### Gap 4: Gradient Descent Monoculture vs. Multi-Algorithm Learning

| Aspect | Current Reality | Clean-Sheet Design |
|--------|-----------------|-------------------|
| Learning algorithm | Backpropagation + variants (Adam, etc.) | Multiple algorithms at multiple timescales |
| Hardware coupling | Tightly coupled to GPU matrix math | Hardware-agnostic |

**What the convention is:** Backpropagation with gradient descent is the *only* viable way to train large neural networks.

**Why it persists:**
- Decades of optimization in software libraries (PyTorch, JAX) and hardware (NVIDIA GPUs) for this specific algorithm.
- It works well enough. When something works, incentives favor incremental improvement over radical alternatives.
- The entire ML research ecosystem (papers, benchmarks, reproducibility) is built around it.
- Lock-in effects: switching costs are enormous because everything downstream depends on differentiability.

**What breaking it would look like:** Training systems using forward-only learning rules, evolutionary methods, Hebbian learning, or combinations thereof. Hardware designed for these alternative algorithms (neuromorphic chips). Models that learn through interaction rather than optimization of a fixed loss function.

**Evidence it could be broken:**
- Forward-Forward algorithm (Hinton, 2022) trains networks without backpropagation.
- Evolutionary strategies have trained neural networks competitively for specific tasks.
- Intel's Loihi and IBM's TrueNorth neuromorphic chips implement spike-based learning without backprop.
- Liquid neural networks adapt after training using differential equation-based dynamics.
- The brain learns without backpropagation. This is the strongest existence proof that gradient descent is not required for intelligence.

### Gap 5: Centralized Mega-Clusters vs. Distributed Intelligence

| Aspect | Current Reality | Clean-Sheet Design |
|--------|-----------------|-------------------|
| Compute infrastructure | Massive centralized data centers | Distributed, federated, heterogeneous |
| Cost structure | $100M+ training runs | Amortized across distributed nodes |
| Resilience | Single point of failure | Fault-tolerant by design |

**What the convention is:** Frontier AI requires billion-dollar centralized compute clusters.

**Why it persists:**
- Synchronous SGD requires high-bandwidth, low-latency interconnects between GPUs.
- Economies of scale favor concentration.
- Current architectures require all parameters to be accessible during training.
- Power and cooling are more efficient at scale.
- Corporate incentives: centralized training creates moats.

**What breaking it would look like:** AI systems trained across thousands of heterogeneous devices (phones, laptops, edge devices, small clusters) using asynchronous algorithms that tolerate high latency and unreliable connections. Knowledge aggregated through model merging, federated learning, or evolutionary combination rather than synchronized gradient updates.

**Evidence it could be broken:**
- The internet itself proves that the most capable information system can be radically decentralized.
- Federated learning (Google's keyboard prediction) already trains models across millions of devices.
- Model merging research shows that separately trained models can be combined into a single better model without joint training.
- Mixture-of-Experts allows scaling model capacity without scaling per-input computation.
- Biological evolution built intelligence without any centralized coordination whatsoever -- billions of independent agents, no shared gradient signal, yet it produced the most capable intelligence known.

---

## Summary: The Five Convention Breaks and Their Potential Impact

1. **Monolith to Ecosystem**: Replace single architectures with heterogeneous module ecosystems. *Impact: More efficient, more adaptable, incrementally improvable systems.*

2. **Batch to Continuous**: Replace the train-then-deploy paradigm with always-learning systems. *Impact: Dramatically reduced total cost of intelligence, real-time adaptation.*

3. **Uniform to Variable Compute**: Replace fixed computation with difficulty-aware resource allocation. *Impact: Orders-of-magnitude efficiency gains on easy problems, better performance on hard ones.*

4. **Gradient Monoculture to Algorithm Diversity**: Replace backprop-only training with multiple learning algorithms matched to problem types. *Impact: Unlock neuromorphic hardware, approach biological efficiency (~20W brain vs. megawatts for training).*

5. **Centralized to Distributed**: Replace mega-clusters with federated, asynchronous training across heterogeneous devices. *Impact: Democratize frontier AI, reduce infrastructure costs, increase resilience.*

The deepest insight from this analysis: **current AI development treats engineering convenience as physical law.** We use Transformers because they fit GPUs, not because attention is the fundamental mechanism of intelligence. We use backpropagation because it's well-implemented, not because it's the only way to learn. We train in batches because it's reproducible, not because intelligence requires a "school phase" before a "work phase."

The history of building hard things -- from cathedrals to spacecraft to semiconductor fabs -- consistently shows that the biggest breakthroughs come not from doing the conventional thing harder (bigger cathedrals, bigger rockets, bigger fabs) but from questioning whether the convention itself is necessary. SpaceX didn't build a bigger expendable rocket; they questioned why rockets had to be expendable. The Wright Brothers didn't build a better balloon; they questioned why flight required lighter-than-air gas.

The equivalent question for AI: **What if intelligence doesn't require a giant monolithic model, trained on centralized compute, using gradient descent, in a single batch phase, with uniform computation per input?** Every one of those constraints is a convention, not a law. The laws say only: represent information efficiently, assign credit for learning, respect thermodynamics, accept that no optimizer is universal, and pay communication costs. Everything else is up for reinvention.

---

## Sources

- [Information Physics of Intelligence (arxiv)](https://arxiv.org/abs/2511.19156)
- [Thermodynamics-Inspired Explanations of AI (PMC)](https://pmc.ncbi.nlm.nih.gov/articles/PMC11385982/)
- [Landauer's Principle (Wikipedia)](https://en.wikipedia.org/wiki/Landauer's_principle)
- [Fundamental Energy Cost of Finite-Time Parallelizable Computing (Nature)](https://www.nature.com/articles/s41467-023-36020-2)
- [Can AI Scaling Continue Through 2030? (Epoch AI)](https://epoch.ai/blog/can-ai-scaling-continue-through-2030)
- [LLM Scaling Laws: Analysis from AI Researchers in 2026](https://research.aimultiple.com/llm-scaling-laws/)
- [Breaking the Sound Barrier (Encyclopedia.com)](https://www.encyclopedia.com/science/encyclopedias-almanacs-transcripts-and-maps/breaking-sound-barrier)
- [Sound Barrier (Wikipedia)](https://en.wikipedia.org/wiki/Sound_barrier)
- [No Free Lunch Theorem (Wikipedia)](https://en.wikipedia.org/wiki/No_free_lunch_theorem)
- [Beyond Backpropagation: Exploring Innovative Algorithms (arxiv)](https://arxiv.org/html/2509.19063v1)
- [Efficient Learning Without Gradient Backpropagation (OpenReview)](https://openreview.net/forum?id=R0YGjmqiwB)
- [Biological vs Artificial Neural Networks (Nature Scientific Reports)](https://www.nature.com/articles/s41598-021-84813-6)
- [Liquid Neural Networks: Architecture That Adapts After Training](https://www.theainewsdigest.com/p/liquid-neural-networks-the-architecture)
- [The Next Architectural Wave: What Comes After Transformers in 2026](https://borealtimes.org/transformer-ai/)
- [SpaceX Starship: Iterative Design Methodology](https://newspaceeconomy.ca/2023/10/28/spacex-starship-iterative-design-methodology/)
- [SpaceX's Use of Agile Methods](https://cliffberg.medium.com/spacexs-use-of-agile-methods-c63042178a33)
- [From Cathedrals to Codebases: The Endurance of Thoughtful Engineering](https://happytechie.substack.com/p/from-cathedrals-to-codebases-the)
- [Semiconductor Design and Manufacturing (McKinsey)](https://www.mckinsey.com/industries/industrials/our-insights/semiconductor-design-and-manufacturing-achieving-leading-edge-capabilities)
- [AI Beyond the Scaling Laws (HEC Paris)](https://www.hec.edu/en/dare/tech-ai/ai-beyond-scaling-laws)
- [A First Principle Approach to Thinking About AI (Medium)](https://eric-sandosham.medium.com/a-first-principle-approach-to-thinking-about-ai-78e910b923f2)
