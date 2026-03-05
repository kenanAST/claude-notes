# Are LLMs Fundamentally Biased Toward the Statistical Mode? A Deep Research Analysis

## Executive Summary

The evidence is overwhelming: **yes, LLMs are architecturally, mathematically, and procedurally biased toward conventional outputs**, and this bias operates at every layer of the system -- from the training objective, through the model architecture, through alignment fine-tuning, all the way to decoding. However, the question of whether this makes them "anti-innovation" is more nuanced. They are not *incapable* of producing novel recombinations, but they are structurally predisposed against the kind of rare, discontinuous, paradigm-breaking ideas that define genuine innovation.

What follows is the evidence, organized by root cause.

---

## 1. The Root Cause: Maximum Likelihood Estimation and Cross-Entropy Loss

### The Mathematical Foundation

The single most important thing to understand is that **LLM training is Maximum Likelihood Estimation (MLE)**. The training objective is to find parameters theta that maximize P(training_data | theta). This is mathematically equivalent to minimizing cross-entropy loss between the model's predicted distribution and the empirical distribution of the training data.

The critical consequence: **MLE inherently assigns higher probability to patterns that appear more frequently in the training data.** A token sequence that appears 10,000 times in the corpus will, all else being equal, receive far higher probability than one that appears 10 times. The model is literally optimized to predict the most statistically likely next token given a context.

This is not a bug -- it is the *entire* training objective. The model is a compression of the statistical regularities of its training corpus.

### Why This Creates a Bias Toward Convention

Cross-entropy loss treats all training examples equally. There is no mechanism in standard LLM training that says "rare but brilliant outputs should be weighted more heavily than common mediocre ones." The loss function is democratic: frequent patterns dominate the gradient signal simply by virtue of appearing more often.

**Key paper:** The mathematical equivalence of MLE and cross-entropy minimization means that LLM training is, at its core, an exercise in learning the central tendency of language use. This was formalized in the "Galton's Law of Mediocrity" paper (Keon et al., arXiv 2509.25767, 2025), which demonstrated that LLMs exhibit a Galton-style regression to the mean in language generation -- privileging high-frequency, statistically probable patterns while suppressing rare or unconventional ones.

---

## 2. The Softmax Bottleneck and Representation Degeneration

### The Architectural Constraint

At each generation step, the model produces logits for every token in its vocabulary, which are converted to probabilities via the softmax function. The softmax forces probabilities to sum to 1, creating a **zero-sum competition** between tokens. High-probability tokens suppress low-probability ones not just relatively but absolutely.

### The Softmax Bottleneck

**Key paper:** Finlayson et al., "Closing the Curious Case of Neural Text Degeneration" (ICLR 2024), proved that the softmax bottleneck -- the fact that the output layer maps from a finite-dimensional hidden state to a probability distribution over the vocabulary -- creates systematic errors. The model cannot perfectly represent all possible probability distributions, and the errors tend to be worst in the tails of the distribution (i.e., precisely where novel and unconventional tokens live).

### Label Bias in Autoregressive Models

Autoregressive generation suffers from **label bias**: the normalization constraint over vocabulary at each decoding step forces the model to distribute probability mass even when the model is uncertain. This leads to miscalibrated distributions that overweight plausible-but-generic continuations.

---

## 3. The Degeneration Problem: Why Maximizing Likelihood Produces Bland Text

### The Likelihood-Quality Mismatch

**Key paper:** Holtzman et al., "The Curious Case of Neural Text Degeneration" (ICLR 2020), demonstrated a counterintuitive and foundational finding: **maximizing output probability produces degenerate text.** Greedy decoding and beam search -- which select the highest-probability sequences -- produce text that is bland, repetitive, and incoherent for open-ended generation.

The core insight: **human-written text does NOT come from the mode of the probability distribution.** There is a positive correlation between likelihood and quality only up to an inflection point, after which the correlation becomes *negative*. The most probable outputs are not the best outputs.

### The Repetition Feedback Loop

Maximization-based decoding creates a positive feedback loop: once a phrase appears, its probability of appearing again increases, leading to degenerate repetition. This is a direct consequence of autoregressive generation -- each generated token becomes part of the context that influences future tokens.

### Implications for Innovation

If the mode of the distribution (the most probable output) is already bland and repetitive, then LLMs must *deviate* from their training objective to produce interesting text. Innovation, by definition, lies in the tails of the distribution -- precisely where the model assigns lowest probability.

---

## 4. RLHF and Alignment: The Second Layer of Convergence

### How Alignment Amplifies the Bias

Even if pre-training creates a broad distribution over possible outputs, **post-training alignment dramatically narrows it.**

**Key paper:** "On the Algorithmic Bias of Aligning Large Language Models with RLHF: Preference Collapse and Matching Regularization" (arXiv 2405.16455) proved that the KL-divergence-based regularization used in standard RLHF has an inherent algorithmic bias. The KL penalty exponentiates population preferences -- effectively raising majority preferences to the 10th or 100th power -- creating a "very peaky distribution" that virtually disregards minority preferences.

This phenomenon is called **preference collapse**: the aligned model converges on a narrow set of outputs that satisfy the majority preference signal, eliminating diversity.

### Typicality Bias in Human Preference Data

**Key paper:** "Verbalized Sampling: How to Mitigate Mode Collapse and Unlock LLM Diversity" (arXiv 2510.01171, 2025) identified the data-level root cause: **typicality bias** in preference data. Human annotators systematically favor familiar, easy-to-read, predictable text over novel or unusual responses. Even when a creative answer is equally correct, annotators lean toward the conventional one.

The reward model then amplifies this bias: it boosts responses the model already considered likely, aggressively sharpening the probability distribution and collapsing creative output to a few dominant, highly predictable responses.

### The Double Bind

This creates a double bind:
1. **Pre-training** optimizes for the statistical center of the training data
2. **RLHF alignment** further narrows the distribution toward majority-preferred (i.e., conventional) outputs
3. The result is a model that is *doubly* biased toward the mode

---

## 5. Empirical Evidence: Homogenization of Creative Output

### The Doshi-Hauser Study (Science Advances, 2024)

**Key paper:** Doshi & Hauser, "Generative AI enhances individual creativity but reduces the collective diversity of novel content" (Science Advances, Vol. 10, 2024).

In a study of 300 participants writing short stories:
- AI-assisted writers produced stories rated as more creative *individually*
- But AI-assisted stories were significantly **more similar to each other** than human-only stories
- This creates a social dilemma: individuals benefit, but collective novelty decreases

### Cross-Model Homogeneity

**Key paper:** Wenger & Kenett, "We're Different, We're the Same: Creative Homogeneity Across LLMs" (arXiv 2501.19361, 2025).

LLM responses are much more similar to other LLM responses than human responses are to each other, even after controlling for response structure. This homogeneity persists *across different models*, suggesting the problem is architectural/training-objective-level, not model-specific.

### The Homogenizing Effect on Human Thought

**Key paper:** "The Homogenizing Effect of Large Language Models on Human Expression and Thought" (arXiv 2508.01491, 2025).

The narrowing trends toward "a historically uneven center, shaped by the norms, values, and perspectives of English-speaking, Global North, and socioeconomically advantaged populations." At scale, statistical mimicry becomes a generative force that privileges fluency, coherence, and central tendencies while marginalizing rare expressions, alternative reasoning styles, and culturally specific voices.

### Creativity in Advertising

**Key paper:** Keon et al., "Galton's Law of Mediocrity" (arXiv 2509.25767, 2025).

When ad concepts were simplified step-by-step, creative features (metaphors, emotions, visual cues) disappeared first while factual content remained -- demonstrating that models inherently favor high-probability information. When asked to regenerate from simplified inputs, models produced lexical variety but failed to recover depth and distinctiveness. Surface novelty masked shallow ideas.

---

## 6. Temperature, Top-p, and Sampling: Do They Actually Help?

### Temperature: The "Creativity Parameter" Myth

**Key paper:** Peeperkorn et al., "Is Temperature the Creativity Parameter of Large Language Models?" (ICCC 2024).

The relationship between temperature and creativity shows only a **weak correlation between temperature and novelty**, alongside a **moderate correlation with incoherence**. Temperature does not unlock creativity -- it adds noise.

The key finding: while increasing temperature seems to explore a larger region of embedding space, **it does not imply accessing a broader slice of the model's probability distribution.** Temperature flattens the distribution but does not reshape it. The same tokens that were unlikely at temperature 1.0 are still relatively unlikely at temperature 1.5 -- they are just slightly less suppressed.

### The Novelty-Coherence Tradeoff

Higher temperature yields:
- Weak positive correlation with novelty
- Moderately negative correlation with coherence
- No statistically significant impact on problem-solving performance in the range 0.0-1.0

The tradeoff is fundamentally unfavorable: to get marginally more novel outputs, you pay a steep price in coherence. **Temperature does not produce innovation; it produces noise that occasionally, by chance, looks innovative.**

### Nucleus Sampling (Top-p)

Holtzman et al.'s nucleus sampling truncates the unreliable tail of the distribution, which improves text quality but does nothing to increase genuine novelty. It is a defensive measure against degeneration, not a creative tool.

### Min-p Sampling: A Partial Solution

**Key paper:** "Turning Up the Heat: Min-p Sampling for Creative and Coherent LLM Outputs" (ICLR 2025 Oral).

Min-p dynamically adjusts the sampling threshold based on model confidence, achieving better quality-diversity tradeoffs than top-p at equivalent diversity levels. However, it still operates within the probability distribution the model has learned -- it cannot access ideas the model never assigned meaningful probability to.

### The Fundamental Limitation of All Sampling Strategies

**All sampling strategies operate on the same learned probability distribution.** They can choose *where* in the distribution to sample from, but they cannot add probability mass to ideas the model never learned to represent. Sampling is selection, not generation. If the distribution does not contain a genuinely novel idea, no sampling strategy will produce it.

---

## 7. Can LLMs Produce Genuinely Novel Ideas?

### The Si et al. Study: Novel Research Ideas

**Key paper:** Si et al., "Can LLMs Generate Novel Research Ideas? A Large-Scale Human Study with 100+ NLP Researchers" (arXiv 2409.04109, 2024).

LLM-generated research ideas were rated as **more novel** than expert-written ideas (p < 0.05) but **weaker on feasibility.** However, the study found that LLMs "quickly plateau in generating unique ideas, producing many duplicates after an initial burst." The novelty may be recombinatorial rather than fundamentally new.

### The Stochastic Parrot Debate

**Key paper:** Bender et al., "On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?" (FAccT 2021).

The authors argued that "the training data for LMs is only form; they do not have access to meaning" -- that apparent understanding exists solely in the mind of the reader, not the model.

**Counterevidence:** Mechanistic interpretability research (e.g., Othello-GPT) has shown that models do form internal world models -- linear representations of board state that are *causal* with respect to model predictions. This challenges the pure "stochastic parrot" view.

### The Nuanced View

The truth appears to lie between the extremes:
- LLMs can recombine existing ideas in novel ways
- They can identify patterns and connections humans might miss due to their breadth of "knowledge"
- They cannot make the kind of creative leaps that require understanding *why* something matters, not just *what* is statistically likely
- Their "novelty" tends to be variation within the space of existing ideas, not expansion of that space

---

## 8. Model Collapse: The Long-Term Convergence Problem

**Key paper:** Shumailov et al., "AI models collapse when trained on recursively generated data" (Nature, 2024).

When models are trained on data that includes outputs from previous model generations, **the tails of the original distribution disappear irreversibly.** Even a tiny fraction of synthetic data (1 in 1,000) can trigger model collapse. The distributions become progressively narrower with each generation, losing lexical, syntactic, and semantic diversity.

This is not merely a training artifact -- it is a mathematical inevitability of recursive maximum likelihood estimation. Each generation's model captures the mode of the previous generation's output, not its full distribution, creating a progressive narrowing toward the statistical center.

### The Hallucination-Creativity Link

**Key paper:** "Does Less Hallucination Mean Less Creativity?" (arXiv 2512.11509, 2025).

Techniques that reduce hallucination (CoVe, DoLa, RAG) may simultaneously reduce creative capacity. This suggests that hallucination and creativity share underlying mechanisms -- both involve deviating from the highest-probability outputs. Suppressing one may suppress the other.

---

## 9. The Autoregressive Architecture: Structural Limitations

### No Planning or Global Reasoning

Autoregressive generation produces one token at a time with no ability to plan ahead or revise. Each token is conditioned on all previous tokens, but the model cannot "see" where it is going. This fundamentally limits the kind of structured, goal-directed creative thinking that characterizes human innovation.

Unlike diffusion models, which maintain a global representation that undergoes iterative refinement, autoregressive models commit to each token irrevocably. A creative human can draft, reconsider, and restructure -- an autoregressive model cannot.

### Exposure Bias and Error Accumulation

During training, the model sees only ground-truth contexts. During generation, it sees its own outputs. Any deviation from training-distribution-like text compounds through subsequent tokens, creating a pressure toward safe, well-trodden sequences that are least likely to trigger cascading errors.

---

## 10. Synthesis: The Full Chain of Bias Toward Convention

The bias toward conventional outputs operates through a complete chain:

1. **Training Data:** Overrepresents common patterns, mainstream perspectives, English-language/Global North viewpoints
2. **Training Objective (MLE/Cross-Entropy):** Mathematically optimizes for the statistical center of the training distribution; frequent patterns dominate the gradient signal
3. **Softmax Bottleneck:** Creates systematic errors worst in the distribution tails where novel ideas live
4. **RLHF Alignment:** KL-divergence regularization exponentiates majority preferences, causing preference collapse
5. **Typicality Bias in Preference Data:** Human annotators systematically prefer familiar, conventional outputs
6. **Autoregressive Architecture:** No planning, no revision, error accumulation pressures toward safe sequences
7. **Decoding/Sampling:** Temperature adds noise, not creativity; all sampling operates within the learned distribution
8. **Recursive Training (Model Collapse):** Each generation narrows the distribution further, irreversibly losing tail diversity

**Every single layer biases toward the center.**

---

## 11. Is This "Anti-Innovation"?

### The Case for "Yes"

- Innovation requires exploring the tails of possibility space; LLMs are optimized for the mode
- LLMs homogenize collective creative output even while enhancing individual performance
- The regression-to-the-mean effect is a mathematical consequence of the training objective, not a fixable bug
- Cultural homogenization toward Global North norms suppresses diverse ways of thinking
- Model collapse means the problem gets worse over time as AI-generated content enters training data

### The Case for "It's Complicated"

- LLMs can produce novel *recombinations* that humans might not think of due to their breadth
- Internal world models suggest something beyond pure statistical mimicry
- LLM-generated research ideas were rated as more novel than expert ideas in controlled studies
- Tools like Verbalized Sampling and Min-p can partially mitigate mode collapse
- LLMs may serve as useful "divergence engines" when combined with human judgment about which deviations are meaningful

### The Bottom Line

LLMs are not "anti-innovation" in the sense of actively preventing innovation. They are **structurally conservative** -- optimized, at every level, for the statistical center of human knowledge as expressed in text. They are powerful tools for interpolation within the known space of ideas but poor tools for extrapolation beyond it. True innovation -- the kind that creates genuinely new conceptual space -- requires something these systems do not have: a reason to care about what has never been said before.

---

## Key Researchers and Papers

| Researcher(s) | Paper | Key Contribution |
|---|---|---|
| Holtzman et al. | The Curious Case of Neural Text Degeneration (ICLR 2020) | Proved likelihood maximization produces degenerate text |
| Finlayson et al. | Closing the Curious Case (ICLR 2024) | Identified softmax bottleneck as cause |
| Bender, Gebru et al. | On the Dangers of Stochastic Parrots (FAccT 2021) | Argued LLMs lack access to meaning |
| Shumailov et al. | AI models collapse (Nature 2024) | Proved recursive training causes irreversible distribution narrowing |
| Doshi & Hauser | Generative AI enhances individual... (Science Advances 2024) | Individual creativity up, collective diversity down |
| Si et al. | Can LLMs Generate Novel Research Ideas? (2024) | LLM ideas rated more novel but less feasible than human ideas |
| Peeperkorn et al. | Is Temperature the Creativity Parameter? (ICCC 2024) | Temperature has only weak correlation with novelty |
| Keon et al. | Galton's Law of Mediocrity (2025) | Formalized LLM regression to the mean |
| Wenger & Kenett | We're Different, We're the Same (2025) | Homogeneity persists across different LLMs |
| arXiv 2508.01491 | Homogenizing Effect on Human Expression and Thought (2025) | Cultural narrowing toward Global North norms |
| arXiv 2510.01171 | Verbalized Sampling (2025) | Identified typicality bias; proposed mitigation |
| arXiv 2405.16455 | Preference Collapse and Matching Regularization (2024) | KL-divergence causes preference collapse in RLHF |
| Nguyen et al. | Min-p Sampling (ICLR 2025 Oral) | Better coherence-diversity tradeoff than top-p |

---

## Sources

- [Verbalized Sampling: How to Mitigate Mode Collapse and Unlock LLM Diversity](https://arxiv.org/abs/2510.01171)
- [On the Algorithmic Bias of Aligning LLMs with RLHF: Preference Collapse](https://arxiv.org/abs/2405.16455)
- [AI models collapse when trained on recursively generated data (Nature)](https://www.nature.com/articles/s41586-024-07566-y)
- [Can LLMs Generate Novel Research Ideas?](https://arxiv.org/abs/2409.04109)
- [Generative AI enhances individual creativity but reduces collective diversity (Science Advances)](https://www.science.org/doi/10.1126/sciadv.adn5290)
- [We're Different, We're the Same: Creative Homogeneity Across LLMs](https://arxiv.org/abs/2501.19361)
- [The Homogenizing Effect of LLMs on Human Expression and Thought](https://arxiv.org/abs/2508.01491)
- [Galton's Law of Mediocrity: Why LLMs Regress to the Mean](https://arxiv.org/html/2509.25767v1)
- [Is Temperature the Creativity Parameter of Large Language Models? (ICCC 2024)](https://computationalcreativity.net/iccc24/papers/ICCC24_paper_70.pdf)
- [The Curious Case of Neural Text Degeneration](https://arxiv.org/abs/1904.09751)
- [Closing the Curious Case of Neural Text Degeneration (ICLR 2024)](https://arxiv.org/abs/2310.01693)
- [On the Dangers of Stochastic Parrots (Bender et al., 2021)](https://dl.acm.org/doi/pdf/10.1145/3442188.3445922)
- [Stochastic Parrot - Wikipedia](https://en.wikipedia.org/wiki/Stochastic_parrot)
- [From Stochastic Parrots to Digital Intelligence (2025)](https://wires.onlinelibrary.wiley.com/doi/10.1002/wics.70035)
- [Turning Up the Heat: Min-p Sampling (ICLR 2025)](https://arxiv.org/abs/2407.01082)
- [Does Less Hallucination Mean Less Creativity?](https://arxiv.org/html/2512.11509)
- [Homogenizing effect of LLMs on creative diversity (ScienceDirect)](https://www.sciencedirect.com/science/article/pii/S294988212500091X)
- [Why can't language models come up with new ideas? (Sean Goedecke)](https://www.seangoedecke.com/why-cant-ais-have-new-ideas/)
- [Actually, Othello-GPT Has A Linear Emergent World Representation (Neel Nanda)](https://www.neelnanda.io/mechanistic-interpretability/othello)
- [Decoding Strategies: How LLMs Choose The Next Word (AssemblyAI)](https://www.assemblyai.com/blog/decoding-strategies-how-llms-choose-the-next-word)
- [Diverse Preference Learning for Capabilities and Alignment](https://arxiv.org/html/2511.08594)
- [Model Collapse - Wikipedia](https://en.wikipedia.org/wiki/Model_collapse)
