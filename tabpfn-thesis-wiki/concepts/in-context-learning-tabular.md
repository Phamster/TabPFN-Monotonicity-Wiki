---
title: In-Context Learning for Tabular Data
tags: [concept, tfm]
---

# In-Context Learning (ICL) for Tabular Data

The mechanism borrowed from LLMs that makes [[prior-fitted-networks]] work: instead of learning task-specific weights, the model receives a labeled training set as part of its input context and produces predictions for new rows in a single forward pass. The transformer's attention mechanism does the "learning" implicitly, conditioned on whatever examples are in context.

## Why context construction turns out to matter so much

Two independent empirical findings in this wiki converge on the same surprising point: the *content and structure of the context window* affects model behavior as much as or more than which underlying TFM architecture you choose.

- **[[resampling-credit-risk-tfm-2026]]**: on credit default data, the context-construction strategy (balanced vs. uniform sampling, context size) explains more variance in AUC-ROC than the choice between five different TFMs.
- **[[kenfack-fair-icl-2025]]**: on fairness benchmarks, an uncertainty-based in-context sample selection strategy improves group fairness without any model retraining, simply by controlling which examples are shown.

This reframes "which TFM should I use" as a secondary question behind "how should I construct the context" — relevant to designing any thesis experiment, since context strategy is a variable you control directly, cheaply, and reproducibly, unlike retraining a foundation model.

## The unexplored third axis

Neither paper above tests **monotonicity** as the outcome variable. If context construction can move accuracy and fairness, the natural next question is whether it can also be used to *reduce* the monotonicity violations documented in [[economic-validity-audit-2026]] — e.g., does deliberately including counterexample-style context rows (rows that demonstrate the correct monotonic direction, similar in spirit to COMET's counterexample-guided training from [[classical-monotonic-nn-methods]], but applied at inference time instead of training time) reduce violation rates? This would be a genuinely novel, cheap-to-run experiment.

## See also
[[prior-fitted-networks]], [[tabular-foundation-models-landscape]], [[monotonicity-constraints]]
