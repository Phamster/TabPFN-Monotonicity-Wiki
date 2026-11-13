---
title: Calibration vs. Discrimination — Two Different Things Regulators Care About
tags: [concept, regulatory, credit-risk]
---

# Calibration vs. Discrimination

A conceptual distinction that runs through the entire thesis but never has its own page. Regulators, model validators, and practitioners use both metrics but often conflate them. Getting this right in the methodology chapter matters.

## What they measure

**Discrimination** (measured by AUC-ROC, Gini coefficient, KS statistic): Does the model correctly *rank* borrowers by riskiness? A model with perfect discrimination assigns the highest PD to every borrower who eventually defaults, and the lowest to every borrower who doesn't. It doesn't matter what the actual PD numbers are — only whether the ordering is correct.

**Calibration** (measured by Brier score, reliability diagrams, ECE): Do the model's predicted probabilities match empirical default rates? A model that says "this borrower has 5% PD" should default about 5% of the time across the population of borrowers it assigns 5% PD. A model can rank borrowers perfectly (AUC = 1.0) while being completely miscalibrated (every score is wrong in absolute terms).

## Why monotonicity affects them differently

**Monotonicity's effect on discrimination is what the PoM metric measures.** Constraining the model to be monotonic in certain features restricts its hypothesis class — it can no longer use non-monotonic patterns that might give it discriminatory advantage. The AUC-PoM measures exactly how much of this discriminatory advantage is lost. Koklev's finding: typically near-zero on large datasets.

**Monotonicity's effect on calibration is less studied but arguably more important for regulatory purposes.** An IRB model's primary regulatory use isn't to rank borrowers (that's more relevant for portfolio management) — it's to produce *calibrated PDs* that feed into capital calculations. If enforcing monotonicity distorts calibration (e.g., compresses scores near the constraint boundary), the capital implications could be significant even if the AUC impact is negligible. The Brier-PoM in the benchmark (`src/metrics.py` already computes this) is the quantitative handle on this risk.

## What TabPFN brings to this

TabPFN is reportedly better calibrated out of the box than XGBoost — this is one of its touted advantages. Whether that calibration advantage survives:
1. Applying the two-stage adapter (Strategy 1)
2. Context engineering (Strategy 3)

...is an empirical question the thesis can answer by comparing Brier scores before and after constraint enforcement. This is already in your metrics code. Make sure the thesis discussion chapter specifically addresses calibration effects separately from discrimination effects — they're not the same result and regulators care about both.

## The EBA angle

EBA Guidelines on PD estimation under the IRB approach explicitly require both components:
- **Discrimination**: adequate model performance, typically validated by AUC/Gini against holdout samples
- **Calibration**: long-run average PD estimates must not be biased; stressed PD estimates for downturn periods must be produced separately

The PoM metric as defined (relative change in AUC) captures only the discrimination dimension. A complete regulatory assessment would also report the Brier-PoM. Include both in the results chapter.

## See also
[[price-of-monotonicity-credit-pd-2026]], [[regulatory-requirements-irb]], [[credit-risk-pd-modeling]], [[instance-wise-monotonic-calibration-2025]]
