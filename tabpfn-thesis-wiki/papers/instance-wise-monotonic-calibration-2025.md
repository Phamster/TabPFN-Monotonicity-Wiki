---
title: "Instance-Wise Monotonic Calibration by Constrained Transformation (MCCT)"
authors: (per arXiv listing)
year: 2025
venue: arXiv
arxiv_id: 2507.06516
tags: [monotonicity, foundational]
---

# Post-hoc monotonic calibration as a constrained transformation

A 2025 paper proposing a family of monotonic post-hoc calibration maps — applied after any model is trained, correcting its output probabilities to be both better calibrated *and* monotonic. This is the calibration-aware version of the post-hoc adapter idea.

## The key insight

Standard calibration methods (Platt scaling, isotonic regression, temperature scaling) optimize for probability calibration but don't enforce monotonicity of the calibrated output with respect to input features. MCCT does both simultaneously: it learns a constrained transformation of the model's raw output scores such that the final probabilities are (a) calibrated (match empirical default rates at each probability level) and (b) monotonic with respect to the original model's score ordering.

The paper frames monotonicity as a **regularization constraint** on the calibration map — a natural and clean framing that doesn't require touching the underlying model at all. This is a different decomposition than the two-stage adapter in [[monotonicity-enforcement-mechanisms]]: instead of constraining the model itself (Stage 1) and adding a correction (Stage 2), MCCT constrains the post-processing step only.

## Relationship to the two-stage adapter (Strategy 1)

MCCT and the two-stage adapter are both post-hoc, non-invasive approaches that don't require model retraining. The difference:
- **Two-stage adapter**: constrains a structural model (LR) and adds the black-box model as a correction term. Monotonicity comes from Stage 1's structure.
- **MCCT**: takes the black-box model's output score as-is, then applies a constrained transformation. Monotonicity comes from the transformation's mathematical form.

The MCCT approach is arguably simpler to implement — it requires only a constrained univariate transformation of the model's output score, rather than a two-model pipeline. A potential weakness: if the black-box model's output scores violate monotonicity with respect to specific input features (which the discrete-choice audit [[economic-validity-audit-2026]] shows they do), a monotonic transformation of those scores doesn't fix the underlying feature-output non-monotonicity — it just ensures the calibration map doesn't introduce additional violations.

## For the thesis

This paper presents a third option in the "how do you make TabPFN monotonic without touching the model" design space, alongside the two-stage adapter (Strategy 1) and context engineering (Strategy 3). It is cheaper to implement than the adapter (a single constrained univariate function) but addresses a slightly different problem (output score monotonicity rather than feature-output monotonicity). Worth mentioning in the methodology chapter as an alternative you chose not to pursue and why.

The calibration angle is also relevant independently: TabPFN is reportedly well-calibrated out of the box (unlike raw XGBoost), but applying any constraint (adapter or MCCT) might affect calibration. A robustness check comparing Brier scores before and after constraint enforcement — which your `src/metrics.py` already computes — is partially motivated by this concern.

## See also
[[monotonicity-enforcement-mechanisms]], [[economic-validity-audit-2026]], [[price-of-monotonicity-credit-pd-2026]]
