---
title: Prior-Fitted Networks (PFNs)
tags: [concept, tfm]
---

# Prior-Fitted Networks

A PFN is a transformer pretrained once on a large collection of *synthetic* datasets sampled from a defined prior (typically random structural causal models), such that at inference time it can approximate Bayesian posterior-predictive inference for a *new* real dataset just by treating that dataset's labeled examples as context — no gradient updates, no per-dataset training. This is the architectural backbone of every model discussed in [[tabular-foundation-models-landscape]].

## Why the prior matters more than it sounds

Because a PFN never sees real-world data during training, its entire inductive bias comes from how the synthetic prior is constructed. This single fact explains three otherwise-separate threads in this wiki:

1. **[[fairpfn-2024-2025]]** modifies the prior to inject protected-attribute causal structure, training the network to predict counterfactually fair outcomes directly.
2. **[[causal-pretraining-fairness-2026]]** asks whether the *unmodified* prior already confers fairness benefits, simply because synthetic SCM-based data is less prone to encoding spurious historical correlations than real-world data.
3. The unsolved analogous question for monotonicity ([[monotonicity-constraints]]): could the prior be modified the same way — generating only SCMs where a specified feature has a monotonic causal effect on the outcome — to produce a "MonotonicPFN"? Nobody has published this, despite the FairPFN precedent showing the *mechanism* (prior modification) works for at least one type of constraint.

## Open questions for this thesis
- Does prior modification generalize from fairness to monotonicity, or are there reasons it wouldn't (e.g., monotonicity is a *deterministic* constraint on the input-output mapping, whereas counterfactual fairness is a *distributional* constraint on causal mechanisms — these might not transfer the same way)?
- How much of TabPFN's behavior on credit data is actually attributable to prior design choices vs. the in-context examples themselves? (Relevant to disentangling [[resampling-credit-risk-tfm-2026]]'s finding that context strategy dominates TFM choice.)

## See also
[[pfn-bayesian-inference-2022]] (the method paper), [[in-context-learning-tabular]], [[tabular-foundation-models-landscape]], [[fairpfn-2024-2025]]
