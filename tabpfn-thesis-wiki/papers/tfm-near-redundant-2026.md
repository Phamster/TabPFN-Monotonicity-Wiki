---
title: "Tabular Foundation Models Are Near-Redundant: Diversity, Ensembling, and the State of the Art"
authors: (per arXiv HTML 2605.18696)
year: 2026
venue: arXiv
arxiv_id: 2605.18696
tags: [tfm, survey]
---

# TFMs produce near-redundant predictions — the ensemble diversity problem

A 2026 benchmark across 153 datasets testing six TFMs (TabPFN v2.5, TabICL v2, and four others) with a striking finding: **the predictions of modern TFMs are near-redundant** — the pool of six models produces highly correlated predictions, and ensembling them cannot exploit diversity that isn't there. On the per-dataset accuracy wins, TabPFN v2.5 led with 52 wins, TabICL v2 had 46, and the remaining four split the rest.

## Relevance to thesis

**Choosing which TFM to test**: If TFMs produce near-redundant predictions on standard benchmarks, then the choice between TabPFN v2.5, TabICL v2, and Mitra for your monotonicity experiments may matter less than it first appears — any of the three would likely give similar monotonicity violation rates, and a result on one generalizes approximately to the others. This is a useful methodological simplification: you don't need to test all six TFMs to make a general claim about the TFM paradigm.

**A caveat worth noting**: Near-redundancy on *accuracy* doesn't necessarily imply near-redundancy on *monotonicity violation rates*. It's possible two models with nearly identical AUC have very different monotonicity properties — one's accuracy comes from good calibrated scores, the other from compensating violations. This would actually be an interesting finding to add to a thesis if you test more than one TFM.

**The architectural diversity is nominal claim**: The paper argues "this diversity is mostly nominal" because all tested models use some variant of ICL over synthetic or curated priors. This supports the theoretical framing in [[prior-fitted-networks]] — the synthetic prior is the mechanism that matters, and all these models share the same fundamental paradigm, just with different engineering choices around scale and pretraining data composition.

## See also
[[tabular-foundation-models-landscape]], [[tabpfn-3-2026]], [[tabpfn-2.5-2025]]
