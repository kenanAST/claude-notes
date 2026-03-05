# Making AI/LLM Agents More Creative, Innovative, and Capable of Discovery

## Research Compilation (as of March 2026)

---

## Table of Contents

1. [The Core Problem: Mode Collapse and Diversity Loss](#1-the-core-problem-mode-collapse-and-diversity-loss)
2. [Chain-of-Thought Variations for Creativity](#2-chain-of-thought-variations-for-creativity)
3. [Tree of Thoughts / Graph of Thoughts](#3-tree-of-thoughts--graph-of-thoughts)
4. [Constitutional AI for Creativity](#4-constitutional-ai-for-creativity)
5. [Multi-Agent Debate and Collaboration](#5-multi-agent-debate-and-collaboration)
6. [Curiosity-Driven Agents](#6-curiosity-driven-agents)
7. [Novelty Search (Kenneth Stanley)](#7-novelty-search-kenneth-stanley)
8. [AI-Assisted Scientific Discovery](#8-ai-assisted-scientific-discovery)
9. [Prompt Engineering for Innovation](#9-prompt-engineering-for-innovation)
10. [Red Teaming as Creativity](#10-red-teaming-as-creativity)
11. [Evolutionary/Genetic Algorithms + LLMs](#11-evolutionarygenetic-algorithms--llms)
12. [Actionable Synthesis: Building a Creative AI Agent](#12-actionable-synthesis-building-a-creative-ai-agent)

---

## 1. The Core Problem: Mode Collapse and Diversity Loss

Before exploring solutions, it is critical to understand the fundamental problem. Research consistently shows:

**The Problem:** At the collective level, LLMs consistently lack idea diversity relative to humans. Multiple independent LLM ideation sessions frequently converge around similar themes and concepts, even when prompted separately. This is "mode collapse" -- the model gravitates toward a narrow band of high-probability outputs.

**Root Cause:** Post-training alignment (RLHF) reduces LLM diversity due to **typicality bias in preference data**. Human annotators systematically favor familiar, well-formed text -- a well-documented phenomenon in cognitive psychology. This preference signal, when used to train the model, collapses its output distribution.

**Societal Risk:** The widespread adoption of LLMs for ideation risks a "tragedy of the commons" -- individuals benefit from AI-assisted ideation while the collective innovation ecosystem suffers from increased homogeneity.

**Critical Nuance:** Larger models within a family often exhibit *less* diversity than smaller counterparts, challenging the assumption that capability scales with creative utility.

### Key Papers
- Meincke, Mollick, Terwiesch (2024) - "Prompting Diverse Ideas: Increasing AI Idea Variance"
- Science Advances (2024) - "Generative AI enhances individual creativity but reduces the collective diversity of novel content"
- Zhang & Yu (2025) - "Verbalized Sampling: How to Mitigate Mode Collapse and Unlock LLM Diversity"

---

## 2. Chain-of-Thought Variations for Creativity

### What Works

**Ordinary Personas + Chain-of-Thought (Best Combination)**
Meincke et al. (2024) found that the single most effective approach combines two mechanisms:

1. **Chain-of-Thought prompting** reduces *fixation* -- the tendency for LLMs to get stuck on dominant ideas. CoT forces structured reasoning that breaks the model out of its most probable path.
2. **Ordinary personas** (e.g., "Zumba-loving college student," "retired librarian") improve *knowledge partitioning* -- they act as diverse sampling cues that activate different regions of the model's knowledge.

**Critical finding:** "Creative entrepreneur" personas (Steve Jobs, Elon Musk) are LESS effective than ordinary personas. The celebrity personas are themselves high-probability outputs and reinforce convergent thinking.

**The combination of Ordinary Personas + CoT can make LLM idea diversity SURPASS human performance** on key metrics.

### Specific Technique: Idea-Then-Revise
Ask the LLM to first generate short idea summaries, then explicitly revise them to be "bolder and more distinct" before finalizing. This yields the largest gains in idea diversity, nearly reaching levels of human group ideation.

### Actionable Implementation
```
Step 1: Assign an ordinary (non-famous) persona with specific traits
Step 2: Ask the model to think step-by-step about the problem space
Step 3: Generate initial ideas
Step 4: Explicitly ask the model to revise ideas to be "bolder, more distinct,
         and more different from each other"
Step 5: Repeat with different ordinary personas to get cross-domain coverage
```

---

## 3. Tree of Thoughts / Graph of Thoughts

### Tree of Thoughts (ToT) - NeurIPS 2023

**Core Innovation:** ToT generalizes Chain-of-Thought by enabling exploration of multiple reasoning paths simultaneously, with self-evaluation and backtracking.

**How it works:**
- At each reasoning step, the model generates multiple candidate "thoughts"
- Each candidate is evaluated (by the model itself or an external evaluator)
- The model can branch (explore multiple paths), prune (abandon poor paths), and backtrack
- Uses BFS or DFS search strategies over the thought tree

**Results:** On Game of 24, achieves 74% success rate (vs. 4% for standard prompting). Effective on tasks requiring non-trivial planning or search: creative writing, crosswords, mathematical reasoning.

**For creativity:** The branching structure prevents premature convergence on a single line of reasoning. The model explicitly explores alternatives rather than committing to its first (most probable) path.

### Graph of Thoughts (GoT) - ETH Zurich

**Extension beyond ToT:** Allows arbitrary graph structures where thoughts can have multiple parents (aggregation). This enables:
- Dynamic programming-style reasoning
- Combining insights from separate reasoning branches
- Non-linear, multifaceted problem-solving

**Key advantage for innovation:** GoT allows "recombination" of ideas from different branches, which is the computational equivalent of combinatorial creativity.

### Actionable Implementation
```
For creative/innovation tasks:
1. Generate 3-5 distinct initial approaches to the problem
2. For each approach, develop 2-3 intermediate reasoning steps
3. Evaluate each path: "Rate this approach 1-10 for novelty and feasibility"
4. For the top paths, generate further refinements
5. CROSS-POLLINATE: Take the best elements from different branches and combine
6. Allow backtracking: "This path isn't working. What's a completely different
   angle?"
```

---

## 4. Constitutional AI for Creativity

### Current State
Constitutional AI (Anthropic, 2022) trains models to self-critique and revise based on high-level principles. The standard approach focuses on safety and harmlessness.

**Gap identified:** No published research specifically applies Constitutional AI to steer models toward creativity or novelty. This is an open research direction.

### Hypothetical Application (Novel Research Direction)
A "creativity constitution" could include principles like:
- "Prefer surprising and non-obvious connections over conventional ones"
- "When generating ideas, ensure each is meaningfully different from the others"
- "Challenge assumptions in the problem statement before solving"
- "Draw from domains that are distant from the problem domain"
- "If your first response feels 'safe' or 'expected,' revise it to be more daring"

### Related Work: Steering and Amplifying Creativity
A 2024 paper "Steering Large Language Models to Evaluate and Amplify Creativity" demonstrates that LLMs can be directed to both assess and boost creative output through targeted steering mechanisms.

### Actionable Implementation
```
System prompt / constitution for creative tasks:
"When generating ideas, follow these principles:
1. NOVELTY FIRST: Each idea must be meaningfully different from conventional
   approaches. If it sounds like something you'd read in a typical blog post,
   discard it.
2. CROSS-DOMAIN: Draw at least one connection from a field unrelated to the
   problem domain.
3. SELF-CRITIQUE FOR CONVENTIONALITY: After generating, ask yourself 'Is this
   surprising?' If not, replace it.
4. QUANTITY BEFORE QUALITY: Generate many candidates, then select for
   interestingness over safety.
5. UNCOMFORTABLE IDEAS: Include at least one idea that feels risky or
   counterintuitive."
```

---

## 5. Multi-Agent Debate and Collaboration

### Key Finding: Multi-Agent Systems Outperform Single Agents for Novelty

**VirSci (Virtual Scientists)** - An LLM-based multi-agent system that mimics teamwork in scientific research. Organizes agents to collaboratively generate, evaluate, and refine research ideas. Results demonstrate that multi-agent collaboration surpasses single-agent methods.

**DMAD (Diverse Multi-Agent Debate)** - ICLR 2025
- **Problem:** Standard multi-agent debate uses the same reasoning methods across agents, even with different personas -- creating a "fixed mental set"
- **Solution:** Each agent uses genuinely *distinct* reasoning strategies, not just different personas
- **Result:** Consistently outperforms self-reflection, standard debate, and other prompting techniques across multiple benchmarks

### Design Principles That Work (Research-Validated)
1. **Enlarge the agent cohort** -- more agents = more diverse ideas
2. **Deepen interaction depth** -- multi-turn refinement significantly improves quality
3. **Broaden persona heterogeneity** -- agents should have genuinely different expertise, not just different names
4. **Increase critic-side diversity** -- having diverse critics in the ideation-critique-revision loop boosts feasibility
5. **Use distinct reasoning strategies** -- don't just assign personas; assign different problem-solving *methods*

### Multi-Agent Research Ideation
Research shows that involving multiple agents with complementary domain expertise and allowing multi-turn refinement significantly improves the quality of generated ideas. The "many heads are better than one" principle is validated by multiple studies.

### Actionable Implementation
```
Agent Architecture for Innovation:
- Agent 1 (Domain Expert): Deep knowledge in the target field
- Agent 2 (Outsider): Expert in an unrelated field, brings lateral thinking
- Agent 3 (Critic): Identifies weaknesses and conventional thinking
- Agent 4 (Synthesizer): Combines ideas from other agents into novel proposals
- Agent 5 (Red Team): Actively tries to break or challenge every idea

Process:
1. Each agent independently generates ideas using different reasoning methods
2. Agents present ideas to each other
3. Critic and Red Team challenge all ideas
4. Synthesizer combines strongest elements across agents
5. Multiple rounds of refinement
6. Final evaluation by all agents
```

---

## 6. Curiosity-Driven Agents

### Foundational Work: Pathak et al. (2017) - Intrinsic Curiosity Module (ICM)

**Core idea:** Curiosity = prediction error. An agent is "curious" about states it cannot predict well. The difference between the predicted next state and the actual next state serves as an intrinsic reward signal.

**Key technical choices:**
- Operates in a learned feature space (not raw pixels) -- ignores irrelevant environmental noise
- Uses self-supervised inverse dynamics model to learn the feature space
- Curiosity signal encourages agents to seek novel experiences and avoid local optima

### CD-RLHF: Curiosity-Driven RLHF (2025, ACL)

**Breakthrough:** Directly addresses the diversity-alignment tradeoff in language model training.

**How it works:**
- Standard RLHF optimizes for human preferences (alignment) but reduces diversity
- CD-RLHF adds an Intrinsic Curiosity Module that estimates the "novelty" of each generated state
- Uses prediction errors from a forward dynamics model as intrinsic reward
- Curiosity signal encourages the model to explore "novel" states less visited during training

**Results:** Significant gains in diversity on multiple metrics while maintaining alignment quality comparable to standard RLHF. Effective on text summarization and instruction following.

**Why this matters:** This is one of the first approaches to directly incorporate novelty-seeking into the RLHF training loop itself, rather than trying to recover diversity post-hoc through prompting.

### Actionable Implementation
At the agent level (without retraining):
```
Pseudo-curiosity for LLM agents:
1. Maintain a memory of previously generated ideas/solutions
2. For each new generation, compute similarity to past outputs
3. Reward/select for ideas that are DISSIMILAR to the memory bank
4. Periodically "forget" old ideas to prevent the memory from becoming
   too constraining
5. Use embedding distance (not surface-level text similarity) to measure
   true semantic novelty
```

---

## 7. Novelty Search (Kenneth Stanley)

### Core Thesis: "Why Greatness Cannot Be Planned"

Kenneth Stanley (now leading the Open-Endedness team at OpenAI) argues for the **"objective paradox"**: the moment you create an explicit objective, you undermine your ability to reach ambitious goals.

**Why:** Ambitious objectives don't illuminate a path to themselves. The gradient of improvement induced by ambitious objectives leads to dead-end local optima. Natural evolution -- the most powerful innovation engine known -- has no final objective.

### Novelty Search Algorithm
- Search with NO objective other than continually finding novel behaviors
- In maze navigation and biped walking tasks, novelty search **significantly outperforms** objective-based search
- The key insight: stepping stones to ambitious goals often look nothing like progress toward those goals

### Quality-Diversity Algorithms: MAP-Elites
**MAP-Elites (Multidimensional Archive of Phenotypic Elites):**
- Maintains an archive organized by behavior dimensions
- For each cell in the behavior space, keeps the highest-performing solution
- New candidates are added if they exhibit novel behavior OR outperform existing elites
- Result: a diverse map of high-quality solutions covering the entire behavior space

**This is the computational version of "explore broadly and keep what's interesting."**

### Open-Ended Evolution and AI-Generating Algorithms
Jeff Clune's **POET (Paired Open-Ended Trailblazer)** generates its own training challenges while learning to solve them, creating an automatic curriculum. Clune advocates for open-ended algorithms as potentially "the fastest path to creating general AI."

### Actionable Implementation
```
Novelty-driven agent design:
1. DO NOT optimize directly for "the best answer"
2. Instead, maintain an archive of diverse solutions
3. Score new candidates on NOVELTY (distance from existing archive)
   as well as quality
4. Use behavior characterization: don't just measure what an idea IS,
   measure what it DOES differently
5. Accept "stepping stones" that don't look like progress but expand
   the space of possibilities
6. Periodically ask: "What's the most different thing I could try next?"
   rather than "What's the best thing I could try next?"
```

---

## 8. AI-Assisted Scientific Discovery

### What Made These Systems Actually Discover New Things

#### AlphaFold (Nobel Prize 2024)
**What it is:** Predicts protein 3D structures from amino acid sequences.

**What made it work (and what's different from a chatbot):**
1. **Domain-specific architecture:** Evoformer processes evolutionary and spatial relationships simultaneously. This is NOT a general-purpose language model.
2. **Grounded in physics and biology:** Physical and biological knowledge is built INTO the architecture, not just present in training data.
3. **Structured output space:** Predicts 3D coordinates, not free-form text. The output space constrains solutions to physically valid structures.
4. **Massive, curated training data:** 170,000 experimentally validated protein structures as ground truth.
5. **Evaluatable outputs:** Every prediction can be checked against reality (experimental validation).

**Key lesson:** Discovery AI systems succeed when they have domain-specific architectures, physically grounded constraints, and evaluatable outputs. Chatbots generate text; discovery systems generate structured predictions that can be verified.

#### GNoME (DeepMind, 2023) - Materials Discovery
**What it is:** Graph neural network that predicts stability of new crystalline materials.

**Results:** 2.2 million new crystal predictions; 380,000 most stable candidates; 736 independently validated by external labs. Equivalent to ~800 years of conventional discovery.

**What made it work:**
1. **Two complementary pipelines:** Structural (variations on known crystals) + Compositional (randomized chemical formulas)
2. **Active learning loop:** Predictions validated by DFT calculations, results fed back into training
3. **Graph representation:** GNNs naturally represent atomic connections
4. **80% accuracy** (up from 50% for previous algorithms)

#### FunSearch (DeepMind, 2024) - Mathematical Discovery
**What it is:** Evolutionary search over programs, using an LLM as a mutation operator.

**This is the most relevant model for creative AI agents.** Key design:
1. **Searches for PROGRAMS, not solutions:** The LLM generates code that describes HOW to solve a problem, not the answer itself
2. **Evaluator guards against hallucination:** Every candidate is automatically verified
3. **Island-based evolutionary method:** Maintains DIVERSE population pools (prevents convergence)
4. **Best-shot prompting:** Feeds highest-performing programs back as context for the LLM to improve on
5. **Minimal skeleton:** Only evolves the critical logic, not boilerplate

**Result:** First LLM-based system to make genuinely new mathematical discoveries (largest improvement to cap set problem bounds in 20 years).

#### The AI Scientist (Sakana AI, 2024-2025)
**What it is:** End-to-end automated scientific research system.

**v1:** Generates ideas, writes code, runs experiments, produces full papers. Cost: ~$15/paper. Quality: "Weak Accept" at ML conferences.

**v2:** Eliminates reliance on human code templates. Uses agentic tree search. Produced the first entirely AI-generated peer-review-accepted workshop paper.

### Pattern Across Successful Discovery Systems
```
All successful AI discovery systems share these properties:
1. STRUCTURED OUTPUT SPACE -- not free-form text generation
2. AUTOMATIC EVALUATION -- every candidate can be verified programmatically
3. ITERATIVE REFINEMENT -- generate-evaluate-improve loops
4. DIVERSITY MAINTENANCE -- explicit mechanisms to prevent convergence
5. DOMAIN GROUNDING -- physics, biology, or mathematics constrains the space
6. SEARCH, NOT GENERATION -- they search through a space of possibilities,
   not just sample from a distribution
```

---

## 9. Prompt Engineering for Innovation

### Verbalized Sampling (Training-Free, Highest Impact)

**Technique:** Instead of asking for one answer, ask the model to generate multiple responses WITH their probabilities.

Example: "Generate 5 possible solutions to X and assign a probability to each based on how likely you think it is."

**Why it works:** Reframes the task from "pick the most typical response" to "surface the distribution." The model taps back into its pre-training diversity rather than collapsing to the RLHF-preferred mode.

**Results:** 1.6-2.1x diversity improvement in creative writing. 2-3x diversity improvement overall. Training-free, model-agnostic, orthogonal to temperature.

### Random Concept Injection

Recent research (2025) on "Addressing LLM Diversity by Infusing Random Concepts" shows that injecting random, unrelated concepts into prompts can break the model out of conventional thinking patterns.

### Min-p Sampling

A sampling method that improves both quality AND diversity compared to top-p, especially at higher temperatures. Sets a minimum probability threshold relative to the top token, naturally adapting the candidate pool size.

### ReAct Framework
Synergizes reasoning and action: the model thinks through problems AND interacts with external tools/environments. Produces more accurate and contextually appropriate outcomes by grounding reasoning in real-world feedback.

### Actionable Prompt Patterns
```
Pattern 1: Verbalized Sampling
"Generate 5 different approaches to [problem]. For each, assign a probability
reflecting how likely a typical expert would suggest it. Then generate 3 more
approaches that would each have less than 5% probability -- the unexpected ones."

Pattern 2: Constraint Randomization
"Solve [problem] but you MUST incorporate [random unrelated concept].
How does this change your approach?"

Pattern 3: Anti-Pattern Prompting
"What are the 3 most conventional solutions to [problem]? Now generate
solutions that violate each of those conventional assumptions."

Pattern 4: Analogical Reasoning Across Domains
"How would [problem] be solved in [unrelated field]? Transfer that approach."

Pattern 5: Idea Decomposition and Recombination
"Break [problem] into its fundamental components. Now recombine those
components in an order or configuration that has never been tried."
```

---

## 10. Red Teaming as Creativity

### OpenAI's Diverse Red Teaming (2024)

**Core insight:** The challenge of red teaming (generating diverse, effective attacks) is structurally identical to the challenge of creative generation (generating diverse, effective ideas).

**Method:**
1. Generate diverse attacker goals (the creative divergence step)
2. Train an RL attacker to achieve those goals (the execution step)
3. **Novelty reward:** Each new attack is rewarded for being different from past attacks
4. **Auto-generated, per-example rewards:** Rather than a generic reward, generate targeted evaluation criteria for each specific case
5. **Multi-step RL:** The attacker iterates, conditioning on past attempts, rewarded for both success AND difference from previous tries

**Why this matters for creativity:** This is a proven framework for generating outputs that are both effective AND diverse. Replace "attack" with "idea" and you have a creativity engine.

### Self-Play Adversarial Language Game (SPAG)

**Approach:** An LLM plays both attacker and defender in an adversarial game, then is reinforced on winning episodes.

**Result:** After 3 epochs of self-play, reasoning performance continuously improves across benchmarks.

**For creativity:** Self-play forces the model to generate increasingly novel strategies (as an attacker) while also building robustness (as a defender). This naturally produces novelty under competitive pressure.

### Actionable Implementation
```
Red-Team-as-Creativity Framework:
1. Generate initial ideas for [problem]
2. Red Team Agent: "Find the fatal flaw or the conventional assumption
   in each idea"
3. Original Agent: "Revise ideas to address the red team critique while
   maintaining novelty"
4. Red Team Agent: "These revised ideas are still too conventional because..."
5. Iterate until the Red Team cannot find conventional assumptions
6. Score final ideas on: effectiveness + distance from initial ideas
```

---

## 11. Evolutionary/Genetic Algorithms + LLMs

### The FunSearch Paradigm (Most Proven)

FunSearch (DeepMind) is the gold standard for combining evolutionary methods with LLMs:
- **LLM as mutation operator:** The LLM generates variations of programs
- **Automatic evaluator:** Every candidate is tested for correctness
- **Island-based evolution:** Maintains multiple separate populations to preserve diversity
- **Best-shot prompting:** Top performers are fed back as examples

### EvoPrompt
Pioneers using LLMs as direct implementers of evolutionary operators (crossover, mutation) within standard EA frameworks. The LLM doesn't just generate candidates -- it performs the evolutionary operations themselves.

### EVOL-RL (2025) - Preventing Cognitive Collapse

**Problem:** Label-free RL methods (like TTRL) suffer from "Cognitive Collapse" -- optimizing for self-consensus traps the model in a degenerative loop, destroying solution diversity.

**Solution:** Two balanced forces:
1. **Selection (Stability):** Majority-voted answer as stabilizing anchor
2. **Variation (Exploration):** Novelty-aware reward scoring each solution by how different its reasoning is from concurrent responses

**Results:** On AIME benchmarks, lifts pass@1 from 4.6% to 16.4% and pass@16 from 18.5% to 37.9%. Prevents diversity collapse AND improves out-of-domain generalization.

### Genetic Prompt Search (GPS)
Applies genetic operations (mutation) to tokens within prompts, continuously evaluating and retaining only best-performing prompts. Evolves the prompt itself, not the model.

### Quality-Diversity for LLMs
MAP-Elites-style approaches can be applied to LLM outputs:
- Define a behavior space (e.g., "topic area" x "level of abstraction" x "domain of analogy")
- For each cell, keep the highest-quality output
- Generate new candidates by mutating existing elites
- Result: a diverse archive of high-quality ideas covering the full space

### Actionable Implementation
```
Evolutionary Idea Generation:
1. INITIALIZATION: Generate N=20 diverse initial ideas (using persona + CoT)
2. EVALUATION: Score each on novelty (distance from others) + quality
3. SELECTION: Keep top 50% as "parents"
4. CROSSOVER: Take two parent ideas, ask LLM to combine their best elements
5. MUTATION: Take a parent idea, ask LLM to make one surprising change
6. DIVERSITY MAINTENANCE: Use island model -- 3 separate populations that
   occasionally exchange ideas
7. REPEAT for K generations
8. ARCHIVE: Keep a MAP-Elites-style archive organized by behavior dimensions
```

---

## 12. Actionable Synthesis: Building a Creative AI Agent

### Architecture: The Novelty-Seeking Innovation Agent

Based on all research reviewed, here is a concrete architecture:

```
┌─────────────────────────────────────────────────┐
│              INNOVATION AGENT                     │
│                                                   │
│  ┌──────────────┐    ┌──────────────────────┐    │
│  │  IDEA POOL   │    │  NOVELTY ARCHIVE     │    │
│  │  (Current    │    │  (MAP-Elites style   │    │
│  │   generation)│    │   behavior map of    │    │
│  │              │    │   all past ideas)    │    │
│  └──────┬───────┘    └──────────┬───────────┘    │
│         │                       │                 │
│  ┌──────▼───────────────────────▼───────────┐    │
│  │          GENERATION ENGINE                │    │
│  │  - Multi-agent with diverse strategies    │    │
│  │  - Ordinary personas + CoT               │    │
│  │  - Verbalized sampling                    │    │
│  │  - Cross-domain analogy injection         │    │
│  │  - Random concept infusion               │    │
│  └──────────────────┬───────────────────────┘    │
│                     │                             │
│  ┌──────────────────▼───────────────────────┐    │
│  │          EVALUATION ENGINE                │    │
│  │  - Novelty score (distance from archive)  │    │
│  │  - Quality score (feasibility, coherence) │    │
│  │  - Red Team challenge                     │    │
│  │  - Automatic verification where possible  │    │
│  └──────────────────┬───────────────────────┘    │
│                     │                             │
│  ┌──────────────────▼───────────────────────┐    │
│  │          EVOLUTIONARY LOOP                │    │
│  │  - Selection: Keep diverse high-scorers   │    │
│  │  - Crossover: Combine elements            │    │
│  │  - Mutation: Surprising modifications     │    │
│  │  - Island model for diversity             │    │
│  └──────────────────────────────────────────┘    │
│                                                   │
└─────────────────────────────────────────────────┘
```

### The 10 Most Actionable Techniques (Ranked by Evidence Strength)

| Rank | Technique | Evidence | Effort to Implement | Impact |
|------|-----------|----------|-------------------|--------|
| 1 | Verbalized Sampling | Strong (2-3x diversity, training-free) | Low (prompt change) | High |
| 2 | Ordinary Personas + CoT | Strong (surpasses human diversity) | Low (prompt change) | High |
| 3 | Multi-agent with diverse reasoning strategies | Strong (ICLR 2025) | Medium (multi-agent setup) | High |
| 4 | Novelty archive + distance scoring | Strong (novelty search literature) | Medium (embedding + storage) | High |
| 5 | Evolutionary loop (generate-evaluate-select-mutate) | Strong (FunSearch, EVOL-RL) | Medium (pipeline) | High |
| 6 | Automatic evaluation/verification | Strong (all discovery systems) | Varies by domain | Critical |
| 7 | Cross-domain analogy injection | Moderate (combinatorial creativity) | Low (prompt change) | Medium-High |
| 8 | Red Team/adversarial critique loop | Moderate (OpenAI red teaming) | Medium (multi-agent) | Medium-High |
| 9 | Min-p sampling (over top-p) | Moderate (sampling research) | Low (parameter change) | Medium |
| 10 | Anti-pattern / constraint prompting | Emerging (random concept research) | Low (prompt change) | Medium |

### Critical Design Principles (From Scientific Discovery Systems)

1. **SEARCH, NOT JUST GENERATE.** The difference between a chatbot and a discovery system is that discovery systems SEARCH through a structured space. They generate many candidates, evaluate them, and iterate.

2. **AUTOMATIC EVALUATION IS NON-NEGOTIABLE.** Every successful discovery system (AlphaFold, GNoME, FunSearch) has an automatic evaluator. Without one, you cannot do iterative improvement.

3. **DIVERSITY IS A FIRST-CLASS OBJECTIVE.** Don't just optimize for quality. Explicitly measure and reward diversity. Use novelty scores, behavior characterization, and archive-based diversity maintenance.

4. **STRUCTURE THE OUTPUT SPACE.** Free-form text generation is the enemy of discovery. Constrain outputs to structured formats that can be evaluated, compared, and recombined.

5. **ITERATE ACROSS MULTIPLE GENERATIONS.** Single-shot generation is inherently limited. The most powerful systems run many generations of generate-evaluate-select-improve.

6. **MAINTAIN POPULATION DIVERSITY.** Use island models, MAP-Elites archives, or novelty rewards to prevent convergence. The moment all your candidates look similar, you've lost.

7. **GROUND IN REALITY.** The best discovery systems connect to external validation (experiments, simulations, formal verification). Agents that only talk to themselves converge on plausible-sounding but unvalidated ideas.

---

## Sources

### Mode Collapse and Diversity
- [Generative AI enhances individual creativity but reduces collective diversity](https://www.science.org/doi/10.1126/sciadv.adn5290) - Science Advances, 2024
- [Verbalized Sampling: Mitigating Mode Collapse](https://arxiv.org/abs/2510.01171) - Zhang & Yu, 2025
- [Addressing LLM Diversity by Infusing Random Concepts](https://arxiv.org/html/2601.18053v1) - 2025
- [NoveltyBench: Evaluating Creativity and Diversity in LLMs](https://arxiv.org/abs/2504.05228) - 2025

### Chain-of-Thought and Prompting
- [Prompting Diverse Ideas: Increasing AI Idea Variance](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4708466) - Meincke, Mollick, Terwiesch, 2024
- [Chain-of-Thought Prompting Guide](https://www.promptingguide.ai/techniques/cot)
- [Steering LLMs to Evaluate and Amplify Creativity](https://arxiv.org/html/2412.06060v1) - 2024
- [Unleashing the potential of prompt engineering for LLMs](https://arxiv.org/abs/2310.14735)

### Tree/Graph of Thoughts
- [Tree of Thoughts: Deliberate Problem Solving](https://arxiv.org/abs/2305.10601) - Yao et al., NeurIPS 2023
- [Demystifying Chains, Trees, and Graphs of Thoughts](https://arxiv.org/html/2401.14295v3) - Besta et al., ETH Zurich
- [Tree of Thoughts Prompting Guide](https://www.promptingguide.ai/techniques/tot)

### Multi-Agent Debate
- [Breaking Mental Set: Diverse Multi-Agent Debate](https://openreview.net/forum?id=t6QHYUOQL7) - ICLR 2025
- [Many Heads Are Better Than One: Multi-Agent Scientific Ideation](https://arxiv.org/abs/2410.09403)
- [Multi-Agent LLM Dialogues for Research Ideation](https://arxiv.org/html/2507.08350v1) - SIGDIAL 2025
- [Multi-Agent Collaboration Mechanisms: A Survey](https://arxiv.org/html/2501.06322v1)

### Curiosity-Driven Agents
- [Curiosity-driven Exploration by Self-supervised Prediction](https://pathak22.github.io/noreward-rl/) - Pathak et al., 2017
- [Curiosity-Driven RLHF](https://arxiv.org/abs/2501.11463) - ACL 2025
- [Large-Scale Study of Curiosity-Driven Learning](https://pathak22.github.io/large-scale-curiosity/) - Pathak et al.

### Novelty Search and Open-Endedness
- [Novelty Search and the Problem with Objectives](https://link.springer.com/chapter/10.1007/978-1-4614-1770-5_3) - Lehman & Stanley
- [Abandoning Objectives: Evolution through Novelty Search Alone](https://www.cs.swarthmore.edu/~meeden/DevelopmentalRobotics/lehman_ecj11.pdf) - Lehman & Stanley
- [Open-endedness: The last grand challenge](https://www.oreilly.com/radar/open-endedness-the-last-grand-challenge-youve-never-heard-of/) - Stanley et al.
- [MAP-Elites: Illuminating search spaces by mapping elites](https://arxiv.org/abs/1504.04909) - Mouret & Clune

### AI Scientific Discovery
- [AlphaFold: Highly accurate protein structure prediction](https://www.nature.com/articles/s41586-021-03819-2) - Nature, 2021
- [GNoME: Scaling deep learning for materials discovery](https://www.nature.com/articles/s41586-023-06735-9) - Nature, 2023
- [FunSearch: Mathematical discoveries from program search](https://www.nature.com/articles/s41586-023-06924-6) - Nature, 2024
- [The AI Scientist](https://sakana.ai/ai-scientist/) - Sakana AI, 2024
- [The AI Scientist-v2](https://github.com/SakanaAI/AI-Scientist-v2) - Sakana AI, 2025
- [Agentic AI for Scientific Discovery: Survey](https://arxiv.org/html/2503.08979v1) - ICLR 2025
- [Isomorphic Labs Drug Design Engine](https://www.isomorphiclabs.com/articles/the-isomorphic-labs-drug-design-engine-unlocks-a-new-frontier)

### Evolutionary Algorithms + LLMs
- [EVOL-RL: Evolving Language Models without Labels](https://arxiv.org/abs/2509.15194) - 2025
- [When LLMs Meet Evolutionary Algorithms](https://spj.science.org/doi/10.34133/research.0646) - 2024
- [Evolutionary Computation and LLMs: A Survey](https://arxiv.org/html/2505.15741v1) - 2025
- [GAAPO: Genetic Algorithmic Applied to Prompt Optimization](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1613007/full)

### Red Teaming
- [Diverse and Effective Red Teaming with Auto-generated Rewards](https://arxiv.org/abs/2412.18693) - OpenAI, 2024
- [Self-Playing Adversarial Language Game Enhances LLM Reasoning](https://arxiv.org/html/2404.10642v1) - 2024
- [Defining LLM Red Teaming](https://developer.nvidia.com/blog/defining-llm-red-teaming/) - NVIDIA

### Novel Research Ideas
- [Can LLMs Generate Novel Research Ideas?](https://arxiv.org/abs/2409.04109) - Si et al., ICLR 2025
- [LLMs can Realize Combinatorial Creativity](https://arxiv.org/abs/2412.14141) - 2024
- [Chain of Ideas: Revolutionizing Research](https://aclanthology.org/2025.findings-emnlp.477.pdf)

### Sampling Methods
- [Min-p Sampling for Creative and Coherent LLM Outputs](https://arxiv.org/pdf/2407.1082) - 2024
- [Automata-Based Steering for Diverse Structured Generation](https://arxiv.org/abs/2511.11018) - 2025
