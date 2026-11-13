---
title: Towards Fair In-Context Learning with Tabular Foundation Models
authors: Kenfack et al.
year: 2025
venue: arXiv
arxiv_id: 2505.09503
tags: [tfm, fairness]
---

# Fair in-context learning — fixing fairness without retraining

Takes a deliberately different approach from FairPFN: instead of modifying the pretraining prior (which requires retraining the whole foundation model), this paper works at *inference time* by controlling which examples get selected into the in-context window. Two contributions stand out: an uncertainty-based sample selection strategy that improves group fairness (as opposed to FairPFN's individual-level counterfactual fairness) without any retraining, and a direct empirical comparison showing this approach Pareto-dominates a naive "correlation remover" preprocessing baseline across several TFMs (TabPFN, TabICL, TabDPT) and benchmark datasets.

Conceptually this treats fairness as a *context engineering* problem rather than a model-architecture problem — consistent with the broader finding (see [[tabular-foundation-models-landscape]] and the credit-risk resampling paper) that how you construct the in-context window matters as much as which TFM you pick.

## Relevance to thesis

This is the more practically deployable of the two fairness-TFM approaches, because it doesn't require access to FairPFN's specialized pretraining checkpoint or retraining infrastructure — relevant if your thesis needs something runnable on a project-finance-scale dataset using off-the-shelf pretrained TFMs. It also opens a natural parallel question for the monotonicity side: can context-construction strategies (rather than constrained pretraining) be used to encourage monotonic behavior at inference time too? That parallel hasn't been tested by anyone yet.

## See also
[[counterfactual-fairness]], [[in-context-learning-tabular]], [[monotonicity-constraints]]
