---
title: Statistical Foundations of Prior-Data Fitted Networks
authors: Nagler
year: 2023
venue: ICML (PMLR 202:25660–25676)
arxiv_id: 2305.11097
tags: [tfm, foundational, theory]
---

# Nagler (2023): why PFNs work, statistically

Checked 2026-11-26 on proceedings.mlr.press (`nagler23a`) and arXiv. Thesis bib key `nagler2023statistical`.

The theory companion to [[pfn-bayesian-inference-2022]]:
- **Sec. 3 (Thm 3.1):** under prior-support conditions the posterior predictive converges almost surely to the
  KL-optimal approximation of the true distribution within the prior's model class.
- **Sec. 4:** the optimal PFN is a KL-optimal approximation of the PPD; the error from a finite number of
  simulated datasets is O_p(m^{-1/2}). The size prior acts as a regulariser on network complexity.
- **Sec. 5 (main claim, frequentist):** a PFN is a **pre-tuned but untrained predictor**. Its variance vanishes
  when its sensitivity to single training rows vanishes (Thm 5.2); its **bias vanishes only if the predictor is
  localised around the test point** (Thm 5.4).
- **Sec. 6:** transformers guarantee vanishing variance but not localisation (Thm 6.2); Sec. 6.4 proposes
  localised PFNs (k-nearest-neighbour context), the idea behind LoCalPFN (Thomas et al. 2024).

## Relevance to thesis
- Theory support for Ch. 3 and `ppd_monotone.tex`: nothing in the large-n argument forces the *local shape*
  of TabPFN's prediction to be monotone, so violations can persist even with plenty of data.
- Gives a principled reason why the context matters (Strategy 3, [[in-context-learning-tabular]]):
  localising the context reduces bias. A monotone-aware context is a different goal, but the same lever.

## See also
[[pfn-bayesian-inference-2022]], [[prior-fitted-networks]], [[monotonicity-enforcement-mechanisms]]
