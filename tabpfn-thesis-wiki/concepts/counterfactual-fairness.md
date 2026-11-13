---
title: Fairness in ML — Group vs. Counterfactual
tags: [concept, fairness]
---

# Fairness in ML

## The classical taxonomy
[[classical-fairness-ml]] establishes the standard three-way split: **pre-processing** (fix the training data — reweighing, disparate impact removal), **in-processing** (modify the training objective with a fairness-constrained loss), and **post-processing** (adjust decision thresholds per group after training, as in Hardt et al.'s equalized-odds method). Lessmann's fairness-in-credit-scoring paper (see [[credit-risk-pd-modeling]]) benchmarks across all three categories and finds fairness improvements generally cost predictive performance and therefore profit — a tradeoff every later paper in this wiki has to contend with.

## Group fairness vs. counterfactual fairness — not the same thing
Most of the classical taxonomy targets **group fairness**: statistical parity of some metric (false positive rate, approval rate, etc.) across demographic groups. **Counterfactual fairness** is a different, individual-level, causal notion: would *this specific person's* prediction change if their protected attribute had been different, holding the causal mechanisms fixed? It aligns more closely with legal anti-discrimination standards (asking "would this person have been treated the same") but requires causal-model knowledge that's often unavailable in practice.

[[fairpfn-2024-2025]] targets counterfactual fairness specifically — and solves the causal-model-knowledge problem by training a PFN to learn the causal mechanism implicitly through synthetic pretraining rather than requiring the practitioner to specify it. [[kenfack-fair-icl-2025]] instead targets group fairness via context-selection, explicitly positioning itself as conceptually distinct from FairPFN for this reason.

## Why this fork matters for a thesis
If the thesis touches fairness at all (e.g., as a secondary contribution alongside monotonicity, or testing whether [[causal-pretraining-fairness-2026]]'s findings replicate on credit data), it needs to be explicit about *which* fairness notion it's targeting — group or counterfactual — since the two existing TFM-fairness papers use genuinely different mechanisms and would need different baselines.

## See also
[[classical-fairness-ml]], [[fairpfn-2024-2025]], [[kenfack-fair-icl-2025]], [[causal-pretraining-fairness-2026]]
