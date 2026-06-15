# ACI: Artificial Collaborative Intelligence (Concept Proposal)

**Status:** Thought experiment / concept repository. Open for discussion.

## The Core Concept: Dual Evolution
In current multi-agent systems, LLMs collaborate via prompts, but once the task is done, the models remain frozen. 

ACI proposes a **Dual Evolution** loop where collaboration is moved from *inference-time* to *training-time*, and the environment evolves alongside the models:
1. **Model Evolution:** The weights of the models update based on collaborative success.
2. **Environment Evolution:** The shared sandbox (tools, scripts, memory) grows and is optimized by the models themselves.

## A Pragmatic Two-Phase Approach
To make this actionable without massive compute, the ACI loop can be split into two phases:

### Phase 1: External Memory & Tool Building (The Sandbox Evolution)
* Place specialized models (Planner, Coder, Critic) in a persistent Linux environment.
* Let them solve tasks, write scripts, and build a library of reusable tools.
* **No weight updates yet.** The "learning" happens purely in the environment. The sandbox becomes a shared external memory (similar to the *Voyager* paper). 

### Phase 2: Weight-Level Collaboration (The Model Evolution)
* Once the environment is rich with generated tools, log the most successful collaborative episodes.
* Use a critic model + human oversight to curate a high-quality dataset.
* Periodically fine-tune (e.g., via LoRA) the models on these logs so that the *dynamics of collaboration* become embedded in their weights.

## The Known Roadblocks
I am sharing this idea fully aware of the major unresolved challenges:

* **The Evaluation Trap (Overfitting):** How do we prove the models learned *general collaboration dynamics* rather than just overfitting to specific tasks within our sandbox?
* **Catastrophic Forgetting:** Fine-tuning continuously on logs will likely cause the base models to forget general knowledge.
* **The Data Bottleneck:** Gathering enough high-quality, human-filtered collaborative episodes to make LoRA effective is slow and labor-intensive.
* **Credit Assignment:** In a multi-agent success, it is mathematically difficult to determine exactly which model's action led to the reward.

## Why share this?
I am an AI observer, not a researcher with massive compute. I am publishing this because I believe the intersection of **Continual Learning**, **Multi-Agent Systems**, and **Environment Co-evolution** is where the next leap lies. 

If you want to discuss this, test Phase 1, or point out related papers (like Reflexion, STaR, or Voyager)—please open an **Issue**.

---
*License: MIT*
