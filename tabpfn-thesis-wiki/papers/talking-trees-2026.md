---
title: Talking Trees — Reasoning-Assisted Induction of Decision Trees for Tabular Data
authors: (per arXiv listing)
year: 2026
venue: arXiv
arxiv_id: 2509.21465
tags: [tfm, monotonicity]
---

# A side note on why constraints matter beyond accuracy

Not primarily a monotonicity paper — it's about using LLM reasoning to assist decision-tree induction — but it makes an explicit, useful observation in its related-work framing: real-world tabular deployments often come with domain context that pure statistical signal misses, including constraints like fairness, safety, and monotonicity, plus application-specific rules imposed by regulation. The paper notes that current in-context-learning TFMs are typically pretrained without these constraints built in, treating it as an open problem rather than solving it.

## Relevance to thesis

Useful as a secondary citation supporting the framing that "TFMs lack mechanisms for regulatory/domain constraints" — it's a general statement of the problem from a different angle (decision tree induction) rather than a worked solution, so it complements rather than competes with the [[economic-validity-audit-2026]] paper, which actually measures and partially fixes the problem.

## See also
[[monotonicity-constraints]], [[tabular-foundation-models-landscape]]
