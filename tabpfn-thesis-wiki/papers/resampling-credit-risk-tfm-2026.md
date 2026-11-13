---
title: Data Presentation Over Architecture — Resampling Strategies for Credit Risk Prediction with Tabular Foundation Models
authors: Tanna et al.
year: 2026
venue: arXiv
arxiv_id: 2605.18635
tags: [tfm, credit-risk]
---

# It's not which TFM you pick — it's how you build the context

An actual empirical benchmark (unlike the speculative paper above) on real credit default datasets (Home Credit, Lending Club). Tests four classical models against five TFMs while systematically varying how the in-context examples are selected (seven different context-construction strategies, e.g., balanced sampling vs. uniform sampling) and how large the context window is (1K to 50K examples).

The central finding: the choice of context-construction strategy explains more variance in predictive performance (AUC-ROC) than the choice of which TFM family to use — balanced/hybrid sampling strategies add several AUC points over naive uniform sampling, and that gap is larger than the spread between different TFMs tested.

## Relevance to thesis

This reframes the right comparison for a thesis benchmark chapter: it's not "TFM vs. XGBoost" in the abstract, it's "TFM + context strategy X vs. XGBoost" — and the context-construction choice is itself a design decision a thesis would need to make and justify, not a detail to wave away. It also connects directly to the fairness side: [[kenfack-fair-icl-2025]] independently arrives at the same insight — that context-window construction is a lever for behavior (there, fairness; here, raw accuracy under class imbalance) — which raises an interesting unexplored question: does context-construction strategy *also* affect monotonicity violations? Nobody has tested that three-way interaction (context strategy × monotonicity × credit risk).

## See also
[[credit-risk-pd-modeling]], [[in-context-learning-tabular]], [[tabular-foundation-models-landscape]]
