---
title: Credit Risk / PD Modeling
tags: [concept, credit-risk]
---

# Credit Risk & PD Modeling — where this wiki connects to the earlier literature pass

This concept page bridges the TFM-specific literature above with the broader credit-scoring and regulatory literature covered earlier in the thesis-planning process (Lessmann's body of work, BaFin/ECB/EBA positions on ML in IRB models).

## The established ML-credit-risk literature
Lessmann, Baesens, Seow & Thomas (2015) is the standard benchmarking reference for classical ML methods (logistic regression, random forests, gradient boosting, SVMs) on credit scoring — predates TFMs entirely. Kozodoi, Jacob & Lessmann (2022) benchmarks the classical fairness taxonomy ([[classical-fairness-ml]]) specifically on credit scoring, finding the same fairness-profit tradeoff that recurs throughout this wiki.

## Where TFMs enter
[[foundation-models-credit-risk-2026]] is the only paper that asks the TFM question directly for credit risk, but it's speculative, not empirical, on the fairness/governance claims it makes. [[resampling-credit-risk-tfm-2026]] is the strongest *empirical* TFM-credit-risk paper, but only on raw predictive performance — it doesn't touch fairness or monotonicity at all. No paper combines TFM + credit risk + fairness, or TFM + credit risk + monotonicity, in one empirical study.

## Why monotonicity is not optional here, unlike in most ML applications
Unlike a generic Kaggle-style classification task, credit risk has a regulatory floor: see [[regulatory-requirements-irb]] for the specific EBA/ECB language. This is what elevates "TFMs sometimes violate monotonicity" (a curiosity in the discrete-choice paper, [[economic-validity-audit-2026]]) into "TFMs may be legally inadmissible as Pillar I models without intervention" in the credit risk context specifically — the same empirical phenomenon, but with categorically higher stakes.

## See also
[[regulatory-requirements-irb]], [[economic-validity-audit-2026]], [[foundation-models-credit-risk-2026]], [[resampling-credit-risk-tfm-2026]]
