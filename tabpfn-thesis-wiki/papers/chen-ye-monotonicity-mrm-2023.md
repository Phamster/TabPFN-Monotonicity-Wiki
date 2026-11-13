---
title: "How to Address Monotonicity for Model Risk Management?"
authors: Chen, Dangxing; Ye, Weicheng
year: 2023
venue: International Conference on Machine Learning (ICML 2023)
arxiv_id: n/a (proceedings.mlr.press vol. 202, pp. 5282-5295)
tags: [monotonicity, credit-risk, regulatory, foundational]
---

# Monotonicity for model risk management — the ICML follow-up to the MNAM paper

The 2023 ICML extension of [[chen-ye-monotonic-nam-2022]]'s work. Where the 2022 paper introduced Monotonic NAMs as an architecture, this paper takes a step back and asks the broader question: in the model risk management framework used by banks and regulators, what does "addressing monotonicity" actually require — and does any single technique fully satisfy it?

## Why this is a different contribution from the 2022 paper

The 2022 ICML paper was an architecture paper: here is a neural network that is monotonic by construction, and it performs well on credit scoring benchmarks. The 2023 paper is a framework paper: it formalizes what regulators and model validators actually need when they say "the model must be monotonic," decomposes this into distinct requirements, and evaluates multiple approaches (not just MNAMs) against each requirement.

This distinction matters for your thesis: if regulators have specific, formal monotonicity requirements (which they do — see [[regulatory-requirements-irb]]), and those requirements have distinct sub-criteria, then "does TabPFN's PoM match XGBoost's" is an incomplete question. The right question is "does the enforcement mechanism satisfy each specific regulatory monotonicity criterion?" This paper gives you the framework to ask that question rigorously.

## Key framing from model risk management

In banking model risk management (SR 11-7, OCC guidelines), a model is expected to behave according to conceptual soundness — meaning its assumptions, logic, and outputs are consistent with domain knowledge and economic theory. Monotonicity is one of the most concrete, testable expressions of conceptual soundness. Chen & Ye frame this as: monotonicity isn't just a nice statistical property, it's a **testable proxy for conceptual soundness** that model validators can verify systematically — which is precisely why regulators care about it and why it shows up in EBA guidance.

## Practical connection to the two-stage adapter (Strategy 1)

The paper's framework (from the citation trail) distinguishes between:
- **Global monotonicity**: the function is monotonic over the entire input space
- **Local monotonicity**: the function is monotonic in the neighborhood of the training data
- **Marginal monotonicity**: increasing a feature marginally always moves the prediction in the right direction

XGBoost's native `monotone_constraints` enforce global monotonicity on the tree structure. The two-stage adapter enforces global monotonicity only on Stage 1 (the sign-constrained LR); Stage 2's correction term could in principle violate monotonicity locally even if Stage 1 globally anchors the direction. This distinction is worth discussing in your methodology chapter — your enforcement is only as global as Stage 1 allows, which is weaker than what XGBoost's native constraint achieves but stronger than nothing.

## Relevance to thesis

This paper should be read before writing the methodology chapter. It provides:
1. The formal vocabulary for what "satisfying monotonicity" means in a model-risk-management context — vocabulary your thesis needs to use precisely
2. A framework for evaluating enforcement mechanisms against specific regulatory criteria, rather than just measuring AUC loss
3. A direct bridge between the ML literature on monotonicity and the banking model risk management literature your regulatory chapter needs to engage with

## See also
[[chen-ye-monotonic-nam-2022]], [[regulatory-requirements-irb]], [[monotonicity-enforcement-mechanisms]], [[classical-monotonic-nn-methods]]
