# Constraint Injection and Eliminative Reasoning: Building Complex Things

## TASK A: FORCED CONSTRAINTS

### Identifying and Banning the Top 3 Standard Approaches

The three most conventional approaches to building complex things:

1. **BANNED: Waterfall/phased planning** -- Define requirements upfront, design, build, test, deploy in sequence.
2. **BANNED: Agile/iterative sprints** -- Break work into short iterations, get feedback, adapt. Scrum, Kanban, etc.
3. **BANNED: Modular decomposition with interface contracts** -- Break the system into modules with clean interfaces, build and test independently, integrate.

All three are now off the table.

### The Hard Edge Case

The constraint demands we solve for the hardest scenario simultaneously:
- Requirements are **unknown** (novel domain, no precedent)
- The team has **never worked together** (no shared context or trust)
- Failure has **catastrophic consequences** (lives, critical infrastructure, irreversible harm)
- Budget is **1/10th normal** (can't afford redundancy, parallel paths, or extensive testing)

This is not hypothetical. This is approximately the situation faced by:
- The Apollo 13 rescue team (novel failure mode, ad-hoc team composition, lives at stake, only the materials already aboard)
- The Healthcare.gov rescue "tech surge" (broken system, strangers thrown together, political catastrophe looming, 6-week deadline)

### What Emerges When Conventional Paths Are Blocked

**Approach: Constraint-Bounded Problem Translation**

Rather than planning (banned), iterating (banned), or decomposing (banned), the pattern that emerges from extreme-constraint case studies is a three-phase method:

#### Phase 1: Ruthless Problem Translation (not "requirements gathering")

Instead of gathering requirements (which assumes you can know them) or iterating toward them (which assumes you have time), you **translate the chaos into the tightest possible problem statement**. Gene Kranz's Apollo 13 team didn't plan, iterate, or decompose modules. They asked: "What do we have? What must be true for the crew to survive? What kills them first?" This is eliminative, not constructive -- you define the problem by what CANNOT be true.

Concretely: List every way the system can fail catastrophically. Rank by time-to-kill. The problem is now defined as "prevent the fastest killer, using only what exists."

This works at 1/10th budget because problem translation is nearly free -- it's pure cognition applied to constraints. It works with strangers because it gives everyone a shared, unambiguous frame without requiring trust or shared history.

#### Phase 2: Inverse Construction (build from the failure modes, not from features)

Instead of decomposing into modules (banned) or building features iteratively (banned), you **construct the system as a set of countermeasures against ranked failure modes**. Each piece of the system exists solely because it prevents a specific catastrophic failure.

This is how the Healthcare.gov rescue worked. The "tech surge" team didn't redesign the architecture or iterate on features. They triaged the ~400 most critical defects ranked by impact, and fixed them in order. The system was "rebuilt" as a series of patches against failure, not as a planned architecture. Within 6 weeks, enrollment jumped from 26,000 to 975,000.

This works at 1/10th budget because you build ONLY what prevents catastrophe -- everything else is cut. There is no feature creep, no nice-to-haves, no architectural elegance.

#### Phase 3: Sacrificial Probing (not prototyping, not testing)

Without budget for proper iteration or testing, you use **sacrificial probes** -- minimal, disposable attempts designed to surface the unknown unknowns as fast as possible. The Manhattan Project ran parallel paths (gaseous diffusion, electromagnetic separation, plutonium) not because they could afford redundancy, but because they couldn't afford the cost of picking wrong. Each path was a probe that revealed whether the physics worked.

SpaceX's Starship approach is similar: build cheap prototypes designed to explode, measure everything. Starship development cost ~$3B over 5 years vs. NASA SLS at ~$23B over 13 years.

At 1/10th budget, you can't afford SpaceX-scale probing. But you CAN afford **cognitive probes**: before building anything, identify the single riskiest assumption and find the cheapest possible way to test whether it's true. A conversation, a sketch, a napkin calculation, a single API call. The probe is sacrificial -- you expect it to fail -- but the failure is informative.

### Summary: The Constraint-Forced Method

| Standard Approach (BANNED) | Replacement Under Extreme Constraint |
|---|---|
| Requirements gathering / planning | Eliminative problem translation (define by what kills you) |
| Iterative sprints with feedback | Inverse construction (build countermeasures to ranked failures) |
| Modular decomposition | Sacrificial probing (cheapest possible test of riskiest assumption) |

---

## TASK B: ELIMINATIVE REASONING

### The Top 3 Competing Explanations for Building Complex Things Successfully

**Approach A: "Good Planning"** -- Success comes from thoroughly understanding requirements, creating detailed plans, and executing against them. Exemplified by NASA's traditional approach, waterfall methodology, detailed architecture documents.

**Approach B: "Rapid Iteration and Feedback"** -- Success comes from building quickly, getting real-world feedback, and adapting. Exemplified by SpaceX, lean startup, agile methodologies.

**Approach C: "Great People"** -- Success comes primarily from having the right individuals with the right skills and judgment. Process and methodology are secondary. Exemplified by Kelly Johnson's Skunk Works, the Healthcare.gov rescue team, Standish Group CHAOS data.

### Pairwise Elimination Tests

#### Test 1: Planning vs. Iteration -- Design an experiment to ELIMINATE one

**The Test:** Find cases where both planning quality and iteration speed were independently measurable, and one factor was present while the other was absent.

**Evidence: NASA SLS vs. SpaceX Starship**

- NASA SLS: Extremely detailed planning, massive requirements documents, exhaustive review processes. 13 years, $23B, limited test flights.
- SpaceX Starship: Minimal upfront planning relative to complexity. Rapid build-test-explode cycles. 5 years, ~$3B, numerous test flights.

If good planning were the primary driver of success, SLS should have dramatically outperformed Starship in reliability and achievement per dollar. It did not. SpaceX achieved comparable or superior results at 1/8th the cost in less than half the time.

**Counter-evidence: Therac-25** -- The Therac-25 radiation therapy machine killed patients because of software race conditions. The team iterated and shipped quickly. They did NOT plan or architect for safety. Hardware interlocks (a "planning" artifact from the Therac-20) would have prevented all deaths. This is a case where lack of planning was catastrophic.

**VERDICT: Neither is eliminated.** Planning is necessary but not sufficient for safety-critical domains. Iteration is necessary but not sufficient for domains where failures kill. The test reveals that **the domain determines which matters more**, not that one is universally superior. Planning dominates when failure is catastrophic and irreversible. Iteration dominates when failure is cheap and reversible.

#### Test 2: Planning vs. Great People -- Design an experiment to ELIMINATE one

**The Test:** Find cases where planning was excellent but people were mediocre, and vice versa. Compare outcomes.

**Evidence: Healthcare.gov (both phases)**

- Phase 1 (launch): Extensive planning, detailed requirements, 55 contractors, $630M budget. The plan existed. The architecture was specified. The result was catastrophic failure -- the site couldn't handle 2,000 concurrent users on launch day.
- Phase 2 (rescue): A small "tech surge" team of talented engineers with NO time to plan. They arrived, triaged, and fixed 400 defects in 6 weeks. No new requirements documents, no architecture redesign. Just great people applying judgment.

This is close to a controlled experiment: same system, same requirements, same political context. The only variable that changed was the people (and the elimination of bureaucratic process). The result: great people without a plan succeeded where good planning without great people failed.

**Additional evidence: Standish Group CHAOS data** -- Every time the team "levels up," the likelihood of project success increases by 23%. From lowest to highest skill teams, there is a 224% increase in chance of success. Meanwhile, the CHAOS 2020 report found that project management tools had a **negative** influence on success.

**VERDICT: Planning is weakened but not fully eliminated.** Great people can succeed without good plans. Good plans cannot succeed without great people. But this doesn't eliminate planning entirely -- it just shows it's not the primary driver.

#### Test 3: Iteration vs. Great People -- Design an experiment to ELIMINATE one

**The Test:** Find cases where iteration was rapid but people were mediocre, and cases where great people had no ability to iterate.

**Evidence: Kelly Johnson's Skunk Works**

The SR-71 Blackbird was designed in ~2 years by 150 engineers. The U-2 went from first sketch to first flight in 8 months. These teams did iterate, but the defining characteristic was tiny teams of exceptional people with extreme autonomy. Other Lockheed divisions with identical iterative processes but without Kelly Johnson's hand-picked teams did not produce comparable results.

**Evidence: The "42% of startups fail from no market need" statistic**

The lean startup methodology is the purest form of "iteration and feedback." Yet 42% of startups that practice it still fail because they're solving the wrong problem. Iteration cannot save you from lack of insight -- which is a people problem (judgment, taste, domain understanding).

**Counter-evidence:** Even the best people cannot build complex software without SOME form of feedback loop. Fred Brooks observed that "plan to throw one away; you will anyhow." Great people still need to test their assumptions against reality.

**VERDICT: Iteration is necessary but insufficient. Great people are necessary and closer to sufficient.** You can have brilliant iteration machinery staffed by mediocre people and produce mediocre results. You cannot have great people with zero feedback and produce great results -- but great people naturally create their own feedback loops (they test, they ask, they observe). Iteration as a formal process is not the driver; the underlying capability of learning from reality is, and that lives in people, not process.

### What Survives Elimination?

**"Great People" is the last approach standing**, but with an important refinement:

It's not just "hire smart people." The evidence reveals a specific cluster of capabilities that matter:

1. **Problem translation ability** -- The capacity to convert ambiguous, chaotic situations into tight, solvable problem statements. (Apollo 13 flight controllers, Healthcare.gov tech surge team.)

2. **Judgment about what NOT to build** -- The ability to eliminate options, not generate them. Kelly Johnson's most important rule was removing bureaucracy, reporting, and unnecessary people. The Healthcare.gov rescue team practiced "ruthless prioritization." 42% of startups fail by building something nobody needs -- a failure of eliminative judgment.

3. **Willingness to be wrong quickly** -- Not "iteration" as a process, but a personal disposition. SpaceX engineers expect prototypes to explode. Apollo 13 controllers tested solutions mentally before committing. This is a character trait, not a methodology.

### What This Reveals About the True Nature of Building Complex Things

The eliminative analysis converges on a surprising conclusion: **building complex things is primarily a problem of elimination, not construction.**

The conventional framing is additive: What features do we need? What should we plan? What should we build? The evidence from extreme cases suggests the real skill is subtractive:

- What can we ELIMINATE from the problem space? (Problem translation)
- What should we NOT build? (Ruthless prioritization)
- What assumptions are WRONG? (Sacrificial probing)
- What process is UNNECESSARY? (Kelly Johnson's rules)

The Manhattan Project succeeded not by having the best plan, but by running parallel paths to eliminate uncertainty about which physics would work. Semmelweis succeeded not by proposing a better theory of disease, but by systematically eliminating competing explanations until only one survived. Apollo 13 succeeded not by iterating on solutions, but by eliminating every option that wouldn't work with the materials at hand.

**The general theory: Building complex things is primarily an eliminative activity performed by people with strong judgment. Plans and processes are scaffolding; the load-bearing structure is human judgment applied to the question "what can we remove, rule out, or stop doing?"**

This explains why adding more process, more tools, and more people to failing projects makes them worse (Brooks's Law, CHAOS report findings on tools). Every addition creates new things that must be evaluated and potentially eliminated. The best builders are the best eliminators.
