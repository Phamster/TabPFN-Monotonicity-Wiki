---
title: "Domain-Constrained Stacking Framework for Credit Default Prediction"
authors: (per MDPI Mathematics listing)
year: 2025
venue: MDPI Mathematics, published October 2025
arxiv_id: n/a (MDPI open access)
tags: [monotonicity, credit-risk]
---

# Domain-constrained stacking ensemble with WoE monotonicity — conceptual predecessor to Strategy 1

A peer-reviewed (MDPI Mathematics, October 2025) paper introducing a multi-stage credit scoring pipeline that systematically embeds domain knowledge — including monotonicity verification — at several points in the modeling pipeline, rather than as a single end-to-end constraint. The pipeline includes: threshold-based outlier removal, target variable redefinition, feature discretization with Weight-of-Evidence (WoE) encoding, Information Value (IV) feature selection, and explicit monotonicity verification of the discretized bins before they enter the stacking ensemble.

## Structural similarity to Strategy 1 (two-stage adapter)

This paper's architecture is the closest traditional-ML analog to the two-stage adapter in [[monotonicity-enforcement-mechanisms]]: both separate the monotonicity guarantee from the flexible prediction step. Here, WoE discretization handles monotonicity at the feature-engineering stage, and the stacking ensemble handles flexible prediction on top. In the adapter design: Stage 1 (sign-constrained LR) handles the monotonicity guarantee, Stage 2 (TabPFN correction) handles flexible prediction on top. The conceptual structure is identical; the implementation is entirely different.

## Why this matters for your positioning

This paper shows that a "constrained structural model + flexible predictor on top" is not a novel concept in credit risk — it has an established prior art in traditional ensembles. Your contribution is asking whether the same two-stage logic (constrained guarantor + flexible corrector) can be applied to a TFM setting where the "flexible corrector" is in-context learning rather than a gradient-trained stacking model, and where the constraints need to be enforced at inference time rather than at training time.

Cite this in the methodology chapter as a conceptual predecessor to Strategy 1, then distinguish by the TFM / ICL paradigm shift.

## WoE and monotonicity — a practical note

WoE encoding is already widely used in practice precisely *because* it naturally enforces monotonic feature-outcome relationships when bins are ordered correctly. It's essentially the industry's default pre-processing approach to monotonicity in traditional scorecards. Your thesis makes the implicit argument that WoE-style monotonicity is insufficient for TFMs (which don't use WoE encoding and receive raw features) — this paper is useful evidence that the industry knows monotonicity matters but currently solves it at the pre-processing stage, not the model stage.

## See also
[[monotonicity-enforcement-mechanisms]], [[price-of-monotonicity-credit-pd-2026]], [[credit-risk-pd-modeling]]
