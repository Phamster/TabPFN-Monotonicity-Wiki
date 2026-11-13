---
title: "Pocket Foundation Models: Distilling TFMs into CPU-Ready Gradient-Boosted Trees"
authors: Tanna, Aditya; Bouarour, Nassim; Bouadi, Mohamed; Sankarapu, Vinay Kumar; Seth, Pratinav
year: 2026 (18 May 2026)
venue: arXiv
arxiv_id: 2605.18654
tags: [tfm]
---

# Distilling a TFM into XGBoost — and a possible fifth monotonicity strategy

Found in the 2026-11-11 gap-watch search. The motivation is speed (a fraud scorer must answer in about 2 ms, TFMs take hundreds of ms on GPU), not monotonicity.

## What it does

The TFM is the teacher; an XGBoost or CatBoost model is the student, trained on the teacher's soft predictions. The key technical point: an in-context learner scoring its own context rows leaks their labels, so the soft targets collapse to near one-hot. The fix is **out-of-fold teacher labelling** (the teacher scores each row with that row held out of the context).

- 153 classification datasets; TabICLv2 distilled into XGBoost keeps about 96.5% of the teacher's AUC at about 2 ms on CPU and slightly beats a tuned CatBoost.
- Gains concentrate on low-dimensional data; on high-dimensional data where the teacher is weak, distillation hurts.
- Code is in the TabTune library (same team as [[resampling-credit-risk-tfm-2026]]).

## Relevance to thesis

The paper never mentions monotonicity, but it suggests a **fifth enforcement strategy**: distil TabPFN-3 into an XGBoost student trained with `monotone_constraints`. The student is monotone by construction (same guarantee as Koklev's GBMs), and it inherits part of the TFM's accuracy.

- Why it is attractive: cheap, uses your existing XGBoost code, and the result is a model validators already know.
- Its PoM would be measured against raw TabPFN-3, which makes it directly comparable to Strategy 1.
- Caveat: the [[economic-validity-audit-2026]] authors report that conventional distillation into a constrained student preserves economic structure but loses accuracy. Expect a trade-off, and test it rather than assume it.
- Remember the out-of-fold labelling, or the student learns from leaked labels.

Status: idea only; discuss with Lessmann whether it goes in or into future work. See [[monotonicity-enforcement-mechanisms]].

## See also
[[monotonicity-enforcement-mechanisms]], [[price-of-monotonicity-credit-pd-2026]], [[tabpfn-2.5-2025]], [[fine-tuning-tfm-2026]]
