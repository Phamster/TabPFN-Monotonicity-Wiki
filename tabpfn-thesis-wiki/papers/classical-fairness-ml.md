---
title: Classical fairness-in-ML foundations (Hardt/Price/Srebro 2016; Kamiran/Calders 2012; Feldman et al. 2015)
authors: Hardt, Price, Srebro (2016); Kamiran, Calders (2012); Feldman, Friedler, Moeller, Scheidegger, Venkatasubramanian (2015)
year: 2012-2016
venue: NeurIPS / KIS / KDD
arxiv_id: 1610.02413 / various
tags: [fairness, foundational]
---

# The three-way taxonomy every fairness paper inherits

Three foundational papers establishing the standard fairness-intervention taxonomy referenced throughout this wiki (and in Lessmann's fairness-in-credit-scoring work — see [[credit-risk-pd-modeling]]).

**Hardt, Price & Srebro (2016)** — defines **equality of opportunity** and **equalized odds** as post-processing interventions: take an already-trained classifier's scores and apply group-specific decision thresholds to equalize error rates across protected groups. Proven optimal among post-processing methods for these specific fairness criteria, at the cost of introducing randomization into individual decisions.

**Kamiran & Calders (2012)** — the canonical **reweighing** pre-processing method: before training, assign each (group, label) combination a weight that compensates for under/over-representation in the historical data, so the resulting trained model is less likely to reproduce the historical bias. Implemented in IBM's AI Fairness 360 toolkit and the most widely cited pre-processing baseline in the field.

**Feldman et al. (2015)** — disparate impact removal via distribution transformation: edits feature distributions so they look statistically identical across protected groups, certifying a quantitative disparate-impact bound.

## Relevance to thesis

This is the classical taxonomy (pre/in/post-processing) that the Lessmann fairness-in-credit-scoring paper benchmarks against, and the same taxonomy that the TFM-fairness papers ([[fairpfn-2024-2025]], [[kenfack-fair-icl-2025]]) implicitly reposition: FairPFN is closest to a *prior-modification* approach (a new category these classical papers don't anticipate, since it happens before pretraining rather than before/during/after task-specific training), while Kenfack et al.'s context-selection approach is a TFM-native reinvention of pre-processing (selecting which *examples* enter the context is analogous to reweighing/resampling the training set). Useful for a literature-review section establishing that the standard fairness taxonomy needs an extra category once foundation models with frozen weights enter the picture.

## See also
[[counterfactual-fairness]], [[fairpfn-2024-2025]], [[kenfack-fair-icl-2025]]
