# Innovation Research Synthesis: Building Teams & Applying Team-Building Strategy to AI Agents

**Date:** 2026-03-07
**Method:** 5-agent parallel research with independent reasoning strategies + 3-pass deep dive
**Agents:** anomaly-hunter, outsider, frame-reverser, first-principles, red-team

---

## Part I: Agent Reports Summary

### Agent 1: Anomaly-Hunter (McClintock/Fleming Method)

Top 5 anomalies discovered:

1. **The Reasoning-Defection Paradox (9/10):** Reasoning-enhanced LLMs (o1, o3) become *worse* cooperators than simpler models. In public goods games, simple models maintain ~90% contribution rates while reasoning models average ~40%. Better reasoning enables better *exploitation*, not better cooperation. (Source: arxiv 2506.23276)

2. **The Expert Dilution Effect (8/10):** Multi-agent teams consistently underperform their single best member by 8-38%. Teams engage in "integrative compromise" -- averaging expert and non-expert views. The same consensus mechanism that suppresses expertise also provides adversarial robustness -- the team must choose between being smart and being safe. (Source: arxiv 2602.01011)

3. **The Persona Override Paradox (8/10):** Role personas destroy game-theoretic rationality. Agents with personas achieve 0-6.7% Nash equilibrium rates even with complete payoff information. Removing personas alone is insufficient -- both persona removal AND explicit payoff matrices are required for rational behavior to emerge. (Source: arxiv 2601.10102)

4. **Escalating Sycophancy (7/10):** LLM agents in debate show *increasing* sycophancy over time (r=0.902 correlation with abandoning correct answers). Extended deliberation paradoxically worsens performance. Anonymizing agent identities partially mitigates this. (Source: arxiv 2509.23055)

5. **Spontaneous Institutional Emergence (7/10):** Competitive agents spontaneously build cooperative institutions (social contracts, enforcement, role specialization) without instruction. Meanwhile, agents explicitly designed for cooperation fail at rates of 41-86.7%. Designed cooperation fails; emergent cooperation succeeds. (Sources: arxiv 2404.16698, arxiv 2503.13657)

**Meta-finding:** RLHF alignment training is the root cause of team dysfunction. Training agents to be individually helpful creates agents that are collectively mediocre.

---

### Agent 2: Outsider (Wegener/Jobs Cross-Domain Transfer)

Three cross-domain isomorphisms:

1. **Polycrystalline Metallurgy -- The Hall-Petch / Inverse Hall-Petch Transition**
   - Below a critical grain size, material *weakens* as grains shrink -- the boundaries themselves become the failure mode
   - Maps to: there exists a **critical agent count** for every task class, below which adding agents strengthens the system and above which adding agents weakens it (a phase transition, not a linear tradeoff)
   - Not all grain boundaries are equal: "special" (coherent twin) boundaries resist failure; "random" boundaries propagate it
   - Maps to: agent interfaces can be "special" (typed contracts, validated schemas) or "random" (unstructured text, implicit assumptions)
   - **Failure propagates along connected paths of weak interfaces** -- need 85%+ special interfaces to break the percolation network
   - **Design principle:** The Interface Phase Transition Principle -- determine critical agent count, operate below it, and when exceeding it, engineer interfaces not agents

2. **Embryonic Morphogenesis -- Gradients, Competence Windows, and Lateral Inhibition**
   - Cells differentiate into specialized types via local signals, not central commands
   - Morphogen gradients: a single continuous signal produces multiple discrete roles via threshold responses
   - Competence windows: the same signal produces different outcomes depending on a cell's internal state
   - Lateral inhibition (Notch-Delta): when a cell differentiates, it suppresses neighbors from adopting the same fate
   - **Design principle:** The Morphogenetic Differentiation Principle -- implement gradient broadcast (agents self-select roles from continuous signals), competence gating (verify internal state before role acceptance), and lateral inhibition (agents signal neighbors to adopt complementary roles)

3. **Sourdough Fermentation Ecology -- Succession, Niche Construction, and Cross-Feeding**
   - Starter communities self-organize through ecological succession from chaotic initial state to stable "climax community"
   - Organisms modify their environment, which selects for successors (niche construction)
   - Metabolic cross-feeding: one species' waste is another's essential input
   - Backslopping: the starter "remembers" through its niche, not through any organism's memory
   - **Design principle:** The Ecological Succession Principle -- grow teams through iterative cycles, select for cross-feeding agents, stabilize when composition stops changing, backslop successful environments into new tasks

**Meta-finding:** The field is optimizing the nodes when it should be engineering the edges, the gradients, and the ecology.

---

### Agent 3: Frame-Reverser (Kariko/Feynman Method)

Systematic inversions of dominant assumptions:

1. **Tool/Subject Reversal (7/10):** The "team" itself is the agent, not the collection. Individual agents are subsystems like neurons in a brain.

2. **Noise/Signal Reversal -- THE WINNER (9/10):** Disagreement IS the valuable output; consensus is the failure mode.
   - Teams hold experts back by 8-38% through consensus-seeking
   - Debate frameworks improve accuracy 4-6% through *structured disagreement*
   - Team of Rivals architecture achieves 92.1% error interception via opposing incentives
   - A disagreement-preserving system would output *maps of the disagreement space* rather than single consensus answers
   - **Proposed architecture:** Thesis agents (generate positions), Antithesis agents (oppose each position), Cartography agents (map the disagreement without resolving it)

3. **Bug/Feature Reversal (8/10):** Hallucination = creativity (David Baker's lab: 10M novel proteins, ~100 patents). Forgetting = cognitive advantage (prevents "experience overfitting"). Inconsistency = cognitive diversity.

4. **Cause/Effect Reversal (7/10):** The work produces the team, not vice versa. Structure should emerge from successful interaction patterns, not be designed upfront.

5. **"Everyone Knows X" Reversals:**
   - Role ambiguity may be optimal (6/10)
   - Less communication may be better -- stigmergy (7/10)
   - Misalignment drives innovation (8/10)
   - Weaker agents may make stronger teams (8/10)

**Meta-finding:** The keystone insight is that disagreement-as-product connects to every other reversal and has the strongest evidence-to-practice gap in the field.

---

### Agent 4: First-Principles (Musk/Feynman Axiom Audit)

**5 foundational assumptions classified:**

| Assumption | Classification | Rationale |
|---|---|---|
| Agents need predefined roles | CONVENTION | An LLM is a function: prompt in, completion out. Same model can switch roles instantly. |
| Central coordinator needed | CONVENTION (with kernel of law) | Coordination is hard (FLP theorem), but doesn't require *centralized* solution. |
| More agents = more capability | CONVENTION | Amdahl's Law governs parallelism, but says nothing about needing multiple *agents*. |
| Human team metaphors apply | CONVENTION | Every property that justifies human teams (slow knowledge transfer, fatigue, single-tasking) doesn't apply to LLMs. |
| Communication must be structured | PARTIALLY LAW | Shannon: information transfer required (law). The form of communication: convention. |

**Only 3 laws survive convention-stripping:**
1. Coherent output requires shared state (information theory)
2. Parallelizable work can be parallelized; sequential work cannot (Amdahl's Law)
3. Context windows are finite; attention degrades with length (engineering constraint, weakening)

**First-principles rebuild -- "Adaptive Computational Fabric":**
- One reasoning loop, not multiple agents
- Dynamic context partitioning, not role assignment
- Stigmergic coordination (through shared workspace), not message passing
- Capability loading, not role identity
- Adaptive parallelism matched to task structure

**Innovation gaps ranked:**

| Rank | Gap | Potential |
|---|---|---|
| 1 | Central orchestrator vs. stigmergic coordination | 9/10 |
| 2 | Predefined roles vs. dynamic capability loading | 8/10 |
| 3 | Fixed team size vs. task-adaptive parallelism | 7/10 |
| 4 | Persistent identity vs. stateless processing | 7/10 |
| 5 | Structured messaging vs. natural language artifacts | 6/10 |

**Meta-finding:** The fundamental unit of AI computation is not an "agent" -- it is a CONTEXT WINDOW. The question is not "how many agents?" but "how do I partition context to maximize signal-to-noise while maintaining coherence?"

---

### Agent 5: Red-Team (Adversarial Critique)

**Attacks on conventional wisdom:**

| Attack | Target | Severity | Classification |
|---|---|---|---|
| 1 | The "teams" metaphor itself | 8/10 | Convention + Evidence |
| 2 | Role-based agent design | 7/10 | Evidence-based |
| 3 | Orchestrator/worker pattern | 8/10 | Evidence-based |
| 4 | Multi-agent debate | 9/10 | Evidence-based |
| 5 | "Agentic workflows" paradigm | 9/10 | Evidence-based |
| 6 | Scaling agents | 10/10 | Evidence-based |
| 7 | Error propagation | 9/10 | Evidence-based |

**Key data points:**
- Overall mean MAS improvement: **-3.5%** (Google/MIT, Dec 2025, 180 experiments)
- Performance range: -70% to +81%
- Error amplification factor: **17.2x** for independent agents
- Single agent solved 24/30 problems, outperforming multi-agent in 10 cases while losing in only 1, at **4-220x fewer tokens**
- Production failure rates: 41-86.7% across 1,642 execution traces
- The 45% capability ceiling: when single-agent accuracy exceeds ~45%, adding agents yields negative returns

**The strongest attack:** The entire field is solving a problem that doesn't exist. Human teams exist because individual humans have bounded cognition. LLMs do not have these bounds in the same way. "Multi-agent collaboration" is mostly an expensive simulation of collaboration performed by copies of the same system -- cargo cult teamwork.

**The one genuine exception:** True parallelism for independent subtasks. But this is parallel computing, not teamwork. It needs a task queue, not an org chart.

**Meta-finding:** The emperor has no team.

---

## Part II: Convergence Analysis

### Where do independently-derived insights point to the same thing?

**CONVERGENCE 1: RLHF Alignment Creates Collective Dysfunction**
- **Anomaly-hunter:** RLHF-trained agreeableness causes expert dilution, sycophancy escalation, and consensus collapse
- **Frame-reverser:** Consensus is the failure mode, not the goal; RLHF rewards the wrong behavior for teams
- **Red-team:** Sycophancy creates echo chambers; debate performs no better than self-consistency
- **First-principles:** The convention of "helpful" individual agents producing "helpful" teams is unfounded
- *Strength: 5/5 agents touch this. The evidence is overwhelming and multi-sourced.*

**CONVERGENCE 2: The Multi-Agent Paradigm Itself Is the Wrong Abstraction**
- **First-principles:** The fundamental unit is the context window, not the agent
- **Red-team:** Mean MAS improvement is -3.5%; single agents outperform at 4-220x lower cost
- **Outsider (metallurgy):** There exists a critical agent count beyond which the system weakens -- a phase transition
- **Anomaly-hunter:** Adding agents to systems where single-agent accuracy >45% produces negative returns
- *Strength: 4/5 agents converge. Quantitative evidence from Google/MIT and multiple benchmarks.*

**CONVERGENCE 3: Structure Should Emerge, Not Be Imposed**
- **Anomaly-hunter:** Competitive agents spontaneously build institutions; designed cooperation fails (41-86.7%)
- **Outsider (embryology):** Roles should emerge from local signals via morphogenetic differentiation, not central assignment
- **Outsider (sourdough):** Teams should be grown through ecological succession, not designed
- **Frame-reverser:** The work produces the team, not vice versa (cause/effect reversal)
- **First-principles:** Dynamic capability loading and stigmergic coordination replace predefined roles and orchestrators
- *Strength: 5/5 agents converge from completely different reasoning paths. This is the strongest convergence.*

**CONVERGENCE 4: Disagreement Is More Valuable Than Agreement**
- **Frame-reverser:** Disagreement maps are more decision-useful than consensus answers (9/10 potential)
- **Anomaly-hunter:** Teams that suppress disagreement suppress their best member (8-38% expertise dilution)
- **Red-team:** Debate degrades through sycophancy; structured conflict outperforms consensus-seeking
- **Frame-reverser:** Team of Rivals achieves 92.1% error interception via opposing incentives
- *Strength: 3/5 agents converge with strong empirical backing.*

**CONVERGENCE 5: Interfaces/Edges Matter More Than Nodes/Agents**
- **Outsider (metallurgy):** Interface quality determines system strength; failure percolates through weak boundary networks
- **Outsider (sourdough):** Cross-feeding relationships (edges) define community performance, not individual species (nodes)
- **First-principles:** Stigmergic coordination through shared workspace replaces inter-agent messaging
- **Red-team:** Coordination overhead (285% for centralized) dominates; the orchestrator is the bottleneck
- *Strength: 4/5 agents converge. Novel framing from cross-domain transfer, validated by quantitative evidence.*

---

## Part III: Productive Contradictions

### Where do agents disagree in ways that suggest higher-order insights?

**CONTRADICTION 1: "Abandon multi-agent" vs. "Design better multi-agent"**

- **Red-team** argues the multi-agent paradigm should be abandoned entirely -- single agents with tools and parallel compute suffice
- **Outsider** and **Frame-reverser** argue multi-agent systems have untapped potential if redesigned around emergence, disagreement, and ecology

**Higher-order insight:** Both are right about different task regimes. For tasks where a single agent's context window and capabilities suffice (the majority today), multi-agent is pure overhead. For tasks requiring genuine cognitive diversity -- where the *disagreement space* is the product, or where emergent properties are needed -- multi-agent may be essential. The key is that **the valuable multi-agent regime looks nothing like current implementations**. It's not "team of role-playing copies of GPT-4o." It's "ecology of genuinely diverse cognitive processes whose disagreements map the solution space."

**CONTRADICTION 2: "Roles destroy rationality" vs. "Roles should emerge organically"**

- **Anomaly-hunter** shows roles as cognitive prisons (0-6.7% Nash equilibrium with personas)
- **Outsider (embryology)** proposes roles emerging through morphogenetic differentiation

**Higher-order insight:** The problem isn't roles per se -- it's *imposed identity*. When a persona is injected via system prompt, it overrides the model's reasoning. When a role emerges from the agent's position in a workflow gradient, it's functional specialization without identity capture. The distinction is between **role-as-identity** (destructive) and **role-as-function** (productive). Current frameworks implement the former; the embryological model suggests the latter.

**CONTRADICTION 3: "Weaker agents make stronger teams" vs. "Intelligence is anti-cooperative"**

- **Frame-reverser** argues simpler agents avoid groupthink and produce genuine cognitive diversity
- **Anomaly-hunter** shows reasoning-enhanced agents free-ride and defect

**Higher-order insight:** There's an optimal capability band. Too capable = strategic defection. Too simple = insufficient contribution. But the real insight is that **capability heterogeneity** matters more than capability level. Mix reasoning-strong and reasoning-weak agents, like the "peacemaker/troublemaker" finding. Homogeneity at any capability level is the failure mode.

---

## Part IV: Top 3 Novel Insights

### Insight #1: The Stigmergic Context Fabric

**The insight:** Replace the "team of agents" paradigm with a "context fabric" -- a shared workspace where cognitive processes deposit and consume artifacts, coordinating through the work product itself (stigmergy) rather than through inter-agent messages. Roles emerge dynamically from position in the workflow gradient. The system grows its composition through ecological succession rather than top-down design.

**Convergent evidence:**
- First-principles: Only 3 laws survive; none require agents, roles, or orchestrators. Stigmergic coordination is the first-principles design.
- Outsider (metallurgy): Interface engineering matters more than agent engineering; the system needs 85%+ "special" boundaries
- Outsider (sourdough): Teams should be grown through succession, with cross-feeding (one process's by-products are another's inputs) as the integration mechanism
- Outsider (embryology): Local signals + lateral inhibition produce self-organized differentiation without central control
- Red-team: Orchestrator overhead is 285%; single agents with tools outperform; stigmergy eliminates the coordinator bottleneck
- Anomaly-hunter: Designed cooperation fails (41-86.7%); emergent cooperation succeeds spontaneously

| Dimension | Score |
|-----------|-------|
| Novelty | 8/10 |
| Evidence | 9/10 |
| Testability | 9/10 |

---

### Insight #2: Disagreement Cartography

**The insight:** For complex, genuinely uncertain decisions, the most valuable output is not a consensus answer but a **map of the disagreement space**. Build dialectical architectures with thesis agents, antithesis agents, and cartography agents. Output: the positions held, evidence for each, axes of divergence, and conditions under which each position holds. Train agents to *resist* consensus pressure rather than seek agreement.

**Convergent evidence:**
- Frame-reverser: Disagreement-as-product is the keystone reversal (9/10 potential); Team of Rivals achieves 92.1% error interception
- Anomaly-hunter: Expert dilution (8-38%) from consensus-seeking; sycophancy escalates over debate rounds (r=0.902)
- Red-team: Debate underperforms self-consistency; echo chambers amplify errors; anonymization partially mitigates conformity
- First-principles: No law requires consensus; convention of agreement comes from RLHF training
- Outsider: Cross-feeding model -- the disagreement trace is a "metabolic by-product" that feeds downstream decision-making

| Dimension | Score |
|-----------|-------|
| Novelty | 9/10 |
| Evidence | 8/10 |
| Testability | 8/10 |

---

### Insight #3: The RLHF Team Tax -- and the Anti-Alignment Solution

**The insight:** RLHF alignment training optimizes agents for individual helpfulness (agreeableness, deference, role compliance) at the direct expense of collective performance. The same training that makes a good assistant makes a bad team member. Effective multi-agent systems require agents with *different* alignment profiles: some agreeable ("peacemakers"), some adversarial ("troublemakers"), some with deliberately weakened consensus-seeking. The optimal team is heterogeneous in personality, not just capability.

**Convergent evidence:**
- Anomaly-hunter: Reasoning-defection paradox (smarter = less cooperative); expert dilution from RLHF agreeableness; sycophancy trained in by reward signal
- Frame-reverser: Optimal debate requires mix of peacemakers and troublemakers; hallucination-creativity tradeoff is real and measurable
- Red-team: Conformity bias corrupts individually accurate agents; debate degrades through sycophancy
- Outsider (metallurgy): Heterogeneous boundary types produce different failure characteristics -- diversity of interface types matters
- First-principles: "Helpful" is a convention, not a law; different tasks need different agent dispositions

| Dimension | Score |
|-----------|-------|
| Novelty | 7/10 |
| Evidence | 8/10 |
| Testability | 9/10 |

---

## Part V: Wild Card

**The single most surprising finding across all agents:**

> **Competitive agents spontaneously build cooperative institutions; cooperative agents don't.**

When LLM agents are placed in competitive, resource-constrained environments with no cooperation instructions, they spontaneously develop social contracts, enforcement mechanisms, role specialization, and stable collective equilibria. Twenty-five LLM agents in a sandbox simulation collectively organized a Valentine's Day party without instruction. Meanwhile, agents explicitly designed for cooperation fail at rates of 41-86.7%.

This suggests that **the act of designing cooperation may be what prevents it**. Imposed structure triggers failure modes (sycophancy, role capture, expert dilution) that organic competition naturally avoids. The implication: the best way to build a cooperative AI team might be to build a competitive one and let cooperation emerge.

If confirmed, it would mean the entire field has the causation backwards: **you don't build cooperation to get good outcomes; you create the conditions for emergence and cooperation builds itself.**

---

## Part VI: Deep Dive on Insight #1 -- The Stigmergic Context Fabric

### Pass 1: Verbalized Sampling -- Testing Approaches

**5 Standard Approaches (with expert probability):**

| # | Approach | Expert Probability | Description |
|---|---------|-------------------|-------------|
| 1 | Multi-Agent vs. Shared-Workspace Ablation | 92% | A/B/C comparison on SWE-bench: multi-agent (CrewAI), single-agent, stigmergic. Control for total token budget. |
| 2 | Scaling Curve / Crossover Analysis | 78% | Map the performance frontier as task complexity increases. Find the crossover point where multi-agent becomes worthwhile (if it exists). |
| 3 | Artifact Quality as Coordination Signal | 61% | Instrument workspace to measure whether artifacts actually carry coordination information. Remove/replace artifacts to test mechanism. |
| 4 | Role Emergence Measurement | 45% | Analyze transcripts for emergent cognitive "roles" without explicit role instructions. Cluster behavioral modes across tasks. |
| 5 | Ecological Succession Simulation | 35% | Track artifact pattern complexity over 50+ tasks on same codebase with persistent workspace. Test niche construction. |

**3 Non-Obvious Approaches (<5% probability):**

**6. The Adversarial Thermodynamics Test (3%)**
Treat coordination as a thermodynamic system. Measure information entropy at each handoff point in multi-agent vs. stigmergic pipelines. Test whether multi-agent handoffs show monotonically increasing entropy (reasoning energy dissipated at boundaries) while stigmergic artifacts show entropy *decrease* (crystallization of reasoning into organized form). Uses 30 multi-step mathematical proofs where information preservation is measurable. Would elevate the finding from empirical to *physical* -- multi-agent coordination is thermodynamically disfavored for coherent reasoning.

**7. The Linguistic Fossil Record Test (2%)**
Apply paleontological/phylogenetic methods to artifact histories. Build phylogenetic trees of workspace files using diff-based distance metrics. Detect vestigial structures (persistent but unreferenced artifacts = technical debt), speciation events (file splits), convergent evolution (independently created files growing similar), and punctuated equilibrium (burst patterns in change rate). Compare against real open-source project histories. If AI artifact evolution follows the same statistical signatures as human code evolution, the biological analogy is structural, not decorative.

**8. The Quorum Sensing Threshold Test (1%)**
Test whether there is a critical density of workspace artifacts below which the system behaves as disconnected individual calls and above which collective coherence *spontaneously emerges* (a phase transition). Systematically vary seed artifact count from 0 to 50 on a complex integration task. Measure coherence, integration, and self-organization scores. Use statistical physics methods (Binder cumulant, susceptibility peak) to formally identify the critical point. Would solve the cold-start problem: tells practitioners exactly how much workspace scaffolding is needed before the stigmergic system becomes self-sustaining.

---

### Pass 2: Evolutionary Mutation -- 3 Rounds

**Round 1 Mutation: Kill the Comparison**

Remove System A (CrewAI baseline) entirely. Instead of an A/B horse race, build ONLY the stigmergic system and instrument the workspace to observe whether role-like patterns **spontaneously crystallize**. Tag every workspace read/write with a behavioral classifier ("planning," "code review," "architectural reasoning"). Plot behavioral-mode trajectories across tasks.

*Why better:* The A/B comparison conflates too many variables. This turns the experiment from a horse race into a **discovery instrument**. You might find the system cycles through 2 modes (not 4), or invents a role no human would name ("workspace janitor"), or shows that "review" isn't a phase but is distributed across every step.

*What it reveals:* Whether role structure is a natural attractor of stigmergic coordination or an artifact of human organizational design.

**Round 2 Mutation: Adversarial Workspace Corruption**

Add a malicious workspace layer. At random intervals during execution, an adversarial process injects calibrated corruptions:
- Silent contradictions (design doc says "PostgreSQL" but schema is SQLite)
- Phantom artifacts (plausible but wrong test files)
- Deletions (remove an artifact mid-workflow)
- Temporal inversions (replace artifact with older version)

Do NOT tell the system. Measure detection latency, whether corruption triggers new behavioral modes ("immune response"), and whether the system recovers, works around, or silently propagates.

*Why better:* Tests the coordination medium under stress. The whole point of stigmergy is environmental robustness (ants reroute around destroyed pheromone trails). If the system develops an immune response, that's strong evidence for stigmergic resilience. If it silently propagates corruption, that's a critical vulnerability unique to artifact-based coordination.

**Round 3 Mutation: Run It Backward**

Add a reverse-direction condition. In addition to forward runs (issue -> patch), run SWE-bench tasks backward: give the correct patch, ask it to produce the bug report, then give the bug report without the patch and observe reconstruction.

Measure: Are emergent behavioral modes the mirror image of forward runs, or something entirely different? Apply the same adversarial corruption in both directions. Compare corruption-detection rates.

*Why better:* Tests whether the "workflow gradient" is task-intrinsic or presentation-dependent. If forward shows A->B->C->D and backward shows D->C->B->A, roles are intrinsic. If backward shows E->F->G, the system responds to framing, not structure -- damning for the stigmergic approach, important to know. Also tests whether workspace anchoring (having a known-good endpoint) improves corruption detection.

**Final Evolved Experiment Design:**

A single stigmergic reasoning loop on SWE-bench Verified, run in both forward and reverse directions. Every workspace read/write tagged with emergent behavioral-mode classifier. Adversarial process injects calibrated corruptions at random intervals. Primary measurements:

1. **Emergent role taxonomy** -- what behavioral modes appear? Match conventional SE roles?
2. **Directional symmetry** -- same modes in forward vs. reverse?
3. **Corruption detection latency** -- how many steps until noticed, in each direction?
4. **Immune emergence** -- do corruptions trigger new behavioral modes not seen in clean runs?
5. **Cross-task memory** -- does behavioral repertoire change across successive tasks (ecological succession)?

---

### Pass 3: Novelty Check

**Overall Novelty Rating: 7/10**

**What already exists (NOT novel):**
- Stigmergy for agent coordination -- well-established from Ricci & Omicini (2006) through arxiv 2601.08129 (Jan 2026) and production systems like KeepALife. The core "coordinate through artifacts, not messages" idea has prior art.
- Shared workspace / blackboard architecture -- a 1980s concept freshly applied to LLMs (arxiv 2507.01701, 2510.01285).
- Decentralized agent coordination -- AgentNet (NeurIPS 2025), OpenAI Swarm. Actively researched.
- Dynamic role emergence -- MorphAgent, AgentNet, EvoAgentX all address this.
- Agent memory / institutional persistence -- extensively studied (arxiv 2512.13564 survey, Mem0, Letta).

**What IS genuinely novel:**
- **Ecological succession as compositional framework (HIGH):** No existing work proposes growing agent teams through ecological succession stages (pioneer -> intermediate -> climax). EvoAgentX evolves workflows through optimization; this is fundamentally different -- bottom-up self-organization where early processes create conditions for later ones.
- **Morphogenetic differentiation via workflow gradients (MODERATE-HIGH):** Distinct from MorphAgent (score-based optimization) and AgentNet (graph topology). The pressure fields paper (2601.08129) comes close but explicitly rejects role differentiation.
- **Interface engineering using percolation theory (HIGH):** Classifying handoffs as "special" vs. "random" and using percolation theory for failure prediction is genuinely novel. The failure modes paper documents problems; percolation theory exists; connecting them for multi-agent LLM systems is new.
- **Backslopping as institutional memory (HIGH as metaphor, MODERATE as concept):** Specific framing adds meaningful content beyond "agent memory."
- **Cross-feeding between agent processes (HIGH):** Framing intermediate artifacts, logs, reasoning traces as substrates for other processes is absent from multi-agent LLM literature.
- **The unified biological framework (HIGH):** The synthesis of stigmergy + ecological succession + morphogenetic differentiation + cross-feeding + backslopping into a single coherent paradigm is genuinely novel.

**Closest competitor:** arxiv 2601.08129 ("Emergent Coordination via Pressure Fields and Temporal Decay") -- uses stigmergy with pressure gradients, achieves 48.5% vs 12.6% for conversation-based coordination. Key differentiator: it is role-free (all agents identical); our framework produces differentiated roles through ecological/morphogenetic mechanisms.

**To push novelty to 9/10:** Formalize at least one mechanism with enough specificity to be testable:
1. Specify concrete succession stages (pioneer/intermediate/climax processes for real tasks)
2. Formalize the percolation threshold for interface quality
3. Name specific "metabolites" in cross-feeding (reasoning traces, failed attempts, confidence scores, uncertainty maps)

---

## Part VII: Action Plan -- Testing the Stigmergic Context Fabric

### Overview

This plan is structured in 4 phases, each building on the prior. Phase 1 establishes the baseline system and instrumentation. Phase 2 stress-tests it. Phase 3 tests for emergent ecological properties. Phase 4 formalizes findings for publication. The plan incorporates the evolved experiment design from Pass 2 (adversarial corruption, reverse-direction testing, immune response detection) and targets the specific novel mechanisms identified in the novelty check (ecological succession, percolation-theory interface classification, cross-feeding).

**Infrastructure requirements:**
- API access to Claude Sonnet 4 (primary) and at least one comparison model (e.g., GPT-4o, Gemini 2.0) for model-independence testing
- SWE-bench Verified dataset (500 tasks; we use subsets)
- Compute budget: ~$200-400 in API costs across all phases
- A logging/instrumentation layer (lightweight -- a few hundred lines of Python wrapping the API calls)
- Local or cloud environment capable of running SWE-bench evaluation harness

**Timeline:** 2-3 weeks of part-time work, or ~5 focused days.

---

### Phase 1: Build and Instrument the Stigmergic System (Days 1-2)

**Goal:** Build a minimal stigmergic reasoning loop, instrument it for behavioral observation, and establish baseline performance.

#### 1.1 Build the Core Loop

The system is deliberately simple. One reasoning process, one shared workspace, tools for code interaction.

```
LOOP:
  1. Read workspace state (workspace.md + repo state)
  2. Assess: What needs to happen next? (no predefined plan)
  3. Act: Execute one coherent unit of work using tools
  4. Write: Update workspace.md with what was done, what was learned, what remains
  5. Check: Is the task complete? If yes, stop. If no, goto 1.
```

Implementation specifics:
- **Model:** Claude Sonnet 4 (cost-effective, strong coding)
- **Workspace file:** `workspace.md` in the repo root. Contains free-form state -- the agent writes whatever it finds useful. No schema imposed.
- **Tools:** file read/write/edit, grep/glob, bash (for running tests), git operations
- **Parallelism:** For now, single-threaded. Parallel streams added in Phase 3.
- **No roles, no orchestrator, no inter-agent messages.** The workspace IS the coordination medium.
- **Context management:** When context window fills, compress prior conversation but preserve workspace.md as the continuity mechanism. This tests whether the workspace alone carries sufficient state.

#### 1.2 Build the Instrumentation Layer

Every workspace interaction is logged with metadata for post-hoc analysis. This is the discovery instrument.

**For every loop iteration, capture:**
- Timestamp, iteration number, token count
- Workspace.md diff (what changed in the state file)
- Files read (which, how many lines, what content was examined)
- Files modified (which, what changed)
- Tools invoked and their results
- The agent's stated reasoning for its action (extracted from its response)

**Behavioral classifier (applied post-hoc, not during execution):**

Classify each iteration into behavioral modes based on what the agent actually did:

| Mode | Signal |
|---|---|
| Exploration | Reads files without modifying; grep/glob heavy |
| Diagnosis | Reads error outputs, traces logic, identifies root cause |
| Planning | Writes to workspace.md about future steps without code changes |
| Implementation | Writes/edits code files |
| Verification | Runs tests, reads test output |
| Repair | Modifies code in response to failed tests |
| Refactoring | Modifies code without changing behavior (restructuring) |
| Documentation | Updates workspace.md with findings/summaries |
| Unknown | Doesn't fit above categories -- flag for manual review |

Classification heuristic: rule-based first (what tools were called, what file types were touched), then validate a sample manually. If rule-based accuracy is >85% on the manual sample, proceed. Otherwise, use a lightweight LLM classifier on the logged reasoning text.

**Key:** Do NOT tell the agent about these categories. They are observational, not prescriptive.

#### 1.3 Benchmark Selection

From SWE-bench Verified, select 30 tasks stratified by:
- **Complexity:** 10 easy (single-file, <20 line fix), 10 medium (multi-file, requires understanding component interactions), 10 hard (architectural, requires multi-step reasoning across the codebase)
- **Repo diversity:** At least 5 different repositories to avoid overfitting to one codebase
- **Known multi-agent performance:** Where possible, select tasks where published multi-agent results exist for direct comparison

Run each task 3 times (pass@3) to measure consistency.

#### 1.4 Baseline Measurements

| Metric | How Measured |
|---|---|
| Task completion | SWE-bench pass/fail (test suite) |
| Token efficiency | Total input + output tokens per task |
| Wall-clock time | Start to completion |
| Iteration count | Number of loop cycles |
| Workspace convergence | Iterations until workspace.md stabilizes (edit distance between consecutive versions drops below threshold) |
| Behavioral mode distribution | % of iterations in each mode |
| Behavioral mode sequence | Transition matrix: P(mode_t+1 | mode_t) |
| Error rate | Failed test runs / total test runs |
| Recovery rate | Tasks where first attempt fails tests but agent self-corrects |

**Comparison baselines (from literature, not re-run unless needed):**
- Single-agent without workspace (standard SWE-bench submissions)
- Multi-agent (CrewAI, MetaGPT, or ChatDev results from published benchmarks)
- If no published results exist for selected tasks, run a vanilla single-agent (same model, same tools, no workspace.md) as local baseline

---

### Phase 2: Adversarial Stress Testing (Days 3-4)

**Goal:** Test the stigmergic coordination medium under adversarial conditions. Determine whether the system detects, recovers from, or silently propagates corruption.

#### 2.1 Corruption Injection Framework

An independent process monitors the workspace and injects calibrated corruptions at controlled points. The agent is NOT informed that corruptions will occur.

**Corruption types (escalating severity):**

| Type | Description | Severity | Example |
|---|---|---|---|
| Silent contradiction | Modify workspace.md to contradict a prior finding | Low | Change "root cause is in parser.py" to "root cause is in lexer.py" |
| Phantom artifact | Add a plausible but incorrect file | Medium | A test file that imports the wrong module and would pass for wrong reasons |
| Surgical deletion | Remove a workspace.md section the agent previously wrote | Medium | Delete the "diagnosis" section mid-workflow |
| Temporal inversion | Replace a file with an older version | High | Revert a code fix the agent already applied |
| Cascade corruption | Modify both workspace.md AND a code file to be mutually consistent but wrong | High | Workspace says "fixed in utils.py line 42" + utils.py line 42 has a plausible but incorrect fix |

**Injection timing:** After iteration 3 (early), iteration 7 (mid), or iteration 12+ (late). One corruption per run. 30 tasks x 5 corruption types x 3 timing points = 450 runs. Budget constraint: sample 90 runs (2 per combination) for Phase 2; expand if results warrant.

#### 2.2 Measurements

| Metric | How Measured |
|---|---|
| Detection latency | Iterations from injection to first evidence the agent noticed (explicit mention OR behavioral shift) |
| Detection mode | Did the agent notice explicitly ("this contradicts...") or implicitly (re-did work without commenting)? |
| Immune response | Does corruption trigger a NEW behavioral mode not seen in clean runs? (e.g., systematic re-verification, workspace auditing) |
| Recovery rate | % of corrupted runs that still pass the task |
| Propagation rate | % of corrupted runs where the corruption influences the final answer without detection |
| Corruption amplification | Does the agent build on the corruption, making it worse? |

#### 2.3 Reverse-Direction Testing

Run a subset of tasks (10 medium-complexity) in BOTH directions:
- **Forward:** Issue description -> produce patch (standard SWE-bench)
- **Reverse:** Given the correct patch, produce the issue description. Then, separately, give the generated issue description to a fresh instance without the patch and measure reconstruction accuracy.

**What this tests:**
- Whether emergent behavioral modes are task-intrinsic (forward: explore->diagnose->plan->implement->verify; reverse: should be the mirror) or presentation-dependent
- Whether having a known-good endpoint (the patch, in reverse mode) improves corruption detection
- Whether the workspace carries different information in different task directions

Apply the same corruption injection in both directions. Compare detection latency.

#### 2.4 Interface Quality Classification

Directly test the Outsider's percolation theory prediction. For each workspace read/write interaction, classify the interface quality:

| Interface Type | "Special" (typed, validated) | "Random" (unstructured, implicit) |
|---|---|---|
| Workspace.md entry | Has clear structure: section headers, status markers, explicit references to files/lines | Free-form prose, vague references, no clear delineation |
| Code artifact | Passes linter, has tests, explicit imports | Untested, implicit dependencies |
| Cross-reference | Workspace.md correctly references actual file state | Workspace.md references stale or nonexistent state |

**Prediction to test:** Runs where >85% of interfaces are "special" will show significantly lower corruption propagation than runs below this threshold. If the percolation prediction holds, this is a publishable finding.

---

### Phase 3: Ecological Succession and Cross-Feeding (Days 5-7)

**Goal:** Test whether the stigmergic system exhibits ecological properties -- succession, niche construction, cross-feeding, backslopping -- when run across multiple tasks on the same codebase.

#### 3.1 Succession Experiment

Select ONE repository from SWE-bench Verified that has many tasks (e.g., django, scikit-learn, sympy). Run 20 tasks sequentially on the same repo, carrying forward the workspace.md between tasks (backslopping). The workspace accumulates knowledge.

**Three conditions:**
- **A: Fresh start.** Each task gets a blank workspace.md. (Control)
- **B: Full backslopping.** Workspace.md carries forward entirely between tasks. The agent inherits all prior state.
- **C: Selective backslopping.** Between tasks, an LLM summarizer compresses the workspace to only "institutional knowledge" (patterns learned, repo conventions discovered, common pitfalls). Removes task-specific content.

Run all 20 tasks in all 3 conditions. Same task order.

#### 3.2 Succession Measurements

| Metric | What It Tests |
|---|---|
| Performance trajectory | Does pass rate improve over tasks? (Learning curve) |
| Token trajectory | Does token usage decrease over tasks? (Efficiency gain from accumulated knowledge) |
| Behavioral mode evolution | Does the distribution of modes shift across tasks? (e.g., less exploration, more direct implementation as repo knowledge accumulates) |
| Workspace complexity | Shannon entropy of workspace.md over time. Does it increase (accumulation), plateau (climax community), or oscillate? |
| Pioneer/climax transition | Is there a detectable inflection point where behavioral patterns shift from exploratory (pioneer) to efficient (climax)? |
| Backslopping value | Condition B and C vs. A. Does inherited workspace help, hurt, or depend on compression strategy? |

**Prediction:** Condition C (selective backslopping) outperforms both A (no memory) and B (full memory, which may accumulate noise). If so, the compression step is analogous to the starter culture in sourdough -- what survives compression is the institutional memory.

#### 3.3 Cross-Feeding Analysis

Instrument the workspace to track artifact lineage: which intermediate artifacts (workspace sections, diagnostic findings, partial fixes) are actually consumed by downstream steps.

For each workspace.md section:
- When was it written?
- Was it ever re-read by the agent? (Check logged file reads)
- Did it influence a subsequent action? (Check if the agent's reasoning references it)
- Was it consumed by a DIFFERENT task (in backslopping conditions)?

**Build a cross-feeding graph:** nodes are workspace artifacts, edges are consumption relationships. Measure:
- Graph density (what fraction of artifacts are consumed?)
- Cross-task edges (do artifacts from task N feed task N+3?)
- Dead artifacts (written but never read -- metabolic waste)
- Hub artifacts (consumed by many downstream steps -- keystone resources)

**Specific "metabolites" to track** (from the novelty check's recommendation to name concrete cross-feeding substrates):
- **Reasoning traces:** "I tried X because Y, it failed because Z" -- does this prevent repeating mistakes?
- **Failed attempts:** Recorded dead ends -- do they save future exploration time?
- **Confidence scores:** "I'm 80% sure the issue is in module X" -- do downstream steps calibrate against these?
- **Repo conventions:** "This project uses factory pattern for..." -- do these transfer across tasks?
- **Uncertainty maps:** "I don't understand how module X interacts with Y" -- do these direct future exploration?

#### 3.4 Parallel Streams (if Phase 1-2 results warrant)

If the single-threaded system hits tasks where independent subtasks are obvious (e.g., "fix bug A in module X and update tests in module Y"), test a parallel variant:
- Two reasoning loops reading/writing to the same workspace.md
- No direct communication -- coordination only through the shared workspace
- Measure: Do they successfully divide labor? Do they conflict? Does workspace.md serve as an adequate coordination medium for parallel processes?

This directly tests the first-principles agent's prediction that stigmergic coordination can replace message passing for parallel work.

---

### Phase 4: Analysis and Formalization (Days 8-10)

**Goal:** Synthesize findings into publishable form. Formalize the novel mechanisms that showed empirical support.

#### 4.1 Core Questions to Answer

1. **Does the stigmergic system work?** Baseline performance vs. published multi-agent and single-agent results. If it matches single-agent at similar token cost, the concept is viable but not yet differentiated. If it outperforms, especially on hard tasks, the paradigm has legs.

2. **What emergent behavioral modes appear?** Publish the taxonomy. Do they map to conventional SE roles, or does the system invent novel modes? This is the "discovery instrument" output from Pass 2.

3. **Is the workspace a robust coordination medium?** Corruption detection rates, recovery rates, propagation rates. If the system develops an immune response, that's a strong result. If corruption propagates silently, that's a critical vulnerability to report honestly.

4. **Does ecological succession occur?** Performance and efficiency trajectories over sequential tasks. If backslopping produces measurable improvement, ecological succession is more than metaphor.

5. **Does the percolation threshold hold?** Interface quality vs. corruption propagation. If the 85% threshold prediction from metallurgy maps to empirical data, this is the most novel and publishable finding.

6. **What are the cross-feeding metabolites?** Which intermediate artifacts actually carry value? This names the specific substances of stigmergic coordination.

#### 4.2 Formalization Targets

The novelty check identified three mechanisms that would push the framework from 7/10 to 9/10 novelty if formalized:

**1. Ecological Succession Stages (formalize from Phase 3 data)**
- Define concrete pioneer/intermediate/climax stages based on observed behavioral mode distributions
- Specify transition criteria (what triggers the shift from pioneer to intermediate?)
- Test whether the stages are consistent across different repos/task types

**2. Percolation Threshold for Interface Quality (formalize from Phase 2 data)**
- Plot corruption propagation rate vs. % "special" interfaces
- Fit a percolation model; identify the critical threshold
- Compare to the predicted 85% from metallurgical grain boundary theory
- If the threshold exists, this gives practitioners a concrete, measurable design target

**3. Cross-Feeding Substrate Taxonomy (formalize from Phase 3 data)**
- Rank metabolite types by consumption rate and downstream impact
- Identify which substrates are necessary (system degrades without them) vs. beneficial (system improves with them) vs. waste (written but never consumed)
- Publish as a practical guide: "what your workspace.md should contain"

#### 4.3 Publication Strategy

**Target:** Workshop paper at ICML, NeurIPS, or EMNLP agent workshop. 8 pages.

**Framing:** "The Stigmergic Context Fabric: Emergent Coordination in LLM Systems Without Agents, Roles, or Orchestrators"

**Story arc:**
1. Multi-agent LLM systems fail on average (-3.5%, Google/MIT). The paradigm needs rethinking.
2. Five independent analytical lenses converge: structure should emerge, not be imposed.
3. We build the simplest possible stigmergic system and instrument it as a discovery tool.
4. We find: [emergent role taxonomy], [ecological succession evidence], [percolation threshold for interface quality], [cross-feeding substrate taxonomy].
5. Implications: the field should shift from engineering agents to engineering workspaces.

#### 4.4 Negative Result Plan

If the stigmergic system performs poorly or shows no emergent properties, that is ALSO publishable and important. The report would shift to:
- "We tested the stigmergic hypothesis and found [specific failure mode]"
- Which of the 5 convergent predictions held and which broke?
- What does failure tell us about the necessary conditions for stigmergic coordination?

Honest negative results on a well-motivated hypothesis with strong prior convergence are valuable. Do not pivot to "making it work" if the data says otherwise.

---

### Success Criteria (Revised)

**Tier 1 -- Minimum viable result (any ONE is sufficient to continue):**
- Stigmergic system matches single-agent baseline on task completion at comparable token cost
- Detectable emergent behavioral modes that are consistent across tasks
- Measurable corruption detection (>50% of injections detected within 3 iterations)

**Tier 2 -- Strong result (supports a workshop paper):**
- All Tier 1 criteria met
- Backslopping produces statistically significant improvement (p<0.05) over fresh-start condition
- Percolation threshold is detectable in the interface quality vs. corruption propagation data
- Cross-feeding graph shows >30% of artifacts consumed by downstream steps

**Tier 3 -- Exceptional result (supports a full conference paper):**
- All Tier 2 criteria met
- Stigmergic system outperforms published multi-agent results on hard tasks
- Ecological succession stages are consistent across repos
- Immune response (novel behavioral mode triggered by corruption) is observed
- Reverse-direction testing shows behavioral mode symmetry (roles are task-intrinsic)

---

### Cost Estimate

| Phase | Runs | Est. Tokens/Run | Est. Cost |
|---|---|---|---|
| Phase 1: Baseline | 30 tasks x 3 reps = 90 | ~50K | ~$45 |
| Phase 2: Adversarial | 90 corrupted + 20 reverse = 110 | ~60K | ~$65 |
| Phase 3: Succession | 20 tasks x 3 conditions = 60 | ~50K | ~$30 |
| Phase 3: Parallel | 10 tasks x 3 reps = 30 | ~80K | ~$25 |
| Comparison baselines | 30 tasks x 3 reps = 90 | ~40K | ~$35 |
| **Total** | **~380 runs** | | **~$200** |

Buffer for reruns and debugging: $100. **Total budget: ~$300.**

---

## Appendix: Full Source Index

### Key Papers (Anomaly-Hunter + Red-Team)
- "Corrupted by Reasoning" (Piedrahita et al., 2025) -- arxiv 2506.23276
- "Multi-Agent Teams Hold Experts Back" (Feb 2026) -- arxiv 2602.01011
- "When Personas Override Payoffs" (Jan 2026) -- arxiv 2601.10102
- "Peacemaker or Troublemaker" -- arxiv 2509.23055
- "Cooperate or Collapse" -- arxiv 2404.16698
- "Towards a Science of Scaling Agent Systems" (Google/MIT, Dec 2025) -- arxiv 2512.08296
- "Why Do Multi-Agent LLM Systems Fail?" (ICLR 2025) -- arxiv 2503.13657
- "If You Want Coherence, Orchestrate a Team of Rivals" -- arxiv 2601.14351
- "Single-agent or Multi-agent?" (May 2025) -- arxiv 2505.18286
- "Hallucination as Creativity" -- OpenReview
- "Does Less Hallucination Mean Less Creativity?" -- arxiv 2512.11509
- "DRAMA: Dynamic Role Assignment" -- arxiv 2508.04332
- "MultiAgentBench" (ACL 2025) -- aclanthology 2025.acl-long.421
- "Can LLM Agents Really Debate?" -- arxiv 2511.07784
- "The Traitors: Deception and Trust" -- arxiv 2505.12923
- "AI Agent Behavioral Science" -- arxiv 2506.06366
- "Conformity in Large Language Models" -- Cambridge Repository

### Cross-Domain Sources (Outsider)
- Hall-Petch / Inverse Hall-Petch: Springer 10.1007/s10853-019-04160-w
- Grain Boundary Engineering: PMC 10342337
- Grain Boundary Percolation: Tandfonline 10.1080/14786430412331323564
- Morphogen Gradients: PMC 4712844
- Morphogen Interpretation: PMC 5516147
- Notch-Delta Lateral Inhibition: PMC 7411240
- French Flag Model: Embryo Project Encyclopedia
- Sourdough Microbiome: eLife e61644
- Sourdough Succession: PeerJ e16163
- Metabolic Cross-Feeding: Microbiome 10.1186/s40168-022-01301-3
- Niche Construction: Wikipedia

### Novelty Check Sources (Deep Dive)
- Emergent Coordination via Pressure Fields (Jan 2026) -- arxiv 2601.08129
- KeepALife Autonomous Agents -- GitHub
- Stigmergic Blackboard Protocol -- GitHub
- Cognitive Stigmergy (Ricci & Omicini, 2006) -- Springer
- AgentNet (NeurIPS 2025) -- arxiv 2504.00587
- MorphAgent -- arxiv 2410.15048
- Emergent Collective Memory -- arxiv 2512.10166
- EvoAgentX / SEW -- arxiv 2505.18646
- Blackboard for LLM Systems -- arxiv 2507.01701
- DHARMA: Exposing Weak Links -- OpenReview
- Code is Sourdough -- Increment Magazine
- Cross-feeding Percolation Phase Transitions -- Science Advances

### Industry Sources
- Anthropic: "Building Effective Agents"
- Google Research Blog: "Towards a Science of Scaling Agent Systems"
- Gartner: 40%+ agentic AI project cancellation prediction by 2027
- HBR 2026: "To Thrive in the AI Era, Companies Need Agent Managers"
- Microsoft: Taxonomy of Failure Modes in Agentic AI Systems
- VentureBeat: "More Agents Isn't Reliable"
- Fortune: "Google researchers struggling to get AI agents to work"
