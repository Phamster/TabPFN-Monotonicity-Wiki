---
title: Weight of Evidence (WoE) Encoding and Monotonicity — The Industry's Traditional Solution
tags: [concept, credit-risk, monotonicity]
---

# WoE Encoding and Monotonicity

Weight of Evidence (WoE) encoding is the financial industry's long-established approach to ensuring monotonic, interpretable feature-target relationships in credit scoring — predating ML by decades. Understanding it is important for positioning your thesis's contribution relative to what banks already do.

## What WoE encoding is

WoE transforms a feature by replacing each value (or bin of values) with the log-odds ratio of defaults to non-defaults in that bin:

`WoE(bin) = ln(P(event in bin) / P(non-event in bin))`

When bins are ordered by WoE value in a monotonically increasing or decreasing direction, the encoded feature is by construction monotonically related to the log-odds of default. Logistic regression trained on WoE-encoded features with properly ordered bins is the textbook credit scorecard — monotonic, interpretable, and regulatory-approved for decades.

## Why WoE solves monotonicity for traditional scorecards but not for TFMs

WoE encoding works because:
1. The monotonicity is enforced at the **data level** (in the feature encoding) before the model ever sees the data
2. The model (logistic regression) is **linear in the encoded features**, so the monotonic encoding directly implies monotonic model output

For TFMs, neither condition holds:
- TFMs receive raw feature values, not WoE-encoded ones
- TFMs are highly non-linear transformers; even if you fed them WoE-encoded features, the non-linear attention mechanism could still violate monotonicity in the output

This is why the [[domain-constrained-stacking-2025]] paper (which uses WoE as its monotonicity mechanism) represents traditional pipeline thinking, while your thesis addresses the TFM paradigm where WoE encoding is not an available tool — TabPFN doesn't support arbitrary feature pre-processing in its in-context learning workflow without careful thought about how the transformed features affect the synthetic prior's expectations.

## The practical implication for constraint specification

When specifying which features to constrain and in which direction (the `mono_map` in `src/datasets.py`), you are in effect making the same decision that a scorecard developer makes when ordering WoE bins. The difference: a WoE developer gets to *see* the empirical WoE values for each bin and verify the ordering makes economic sense before fitting the model. Your constraint specification is made a priori based on domain knowledge, then the model is constrained to respect it regardless of what the data says.

This is actually a stronger form of monotonicity enforcement than WoE (you can't override it empirically) but also more brittle (if your economic reasoning is wrong, the constraint hurts more than it helps). This distinction is worth a sentence or two in the methodology chapter when you explain the constraint specification decisions.

## Where to cite this in the thesis

In the "related work" section on how the industry currently handles monotonicity, WoE-based scorecards should be the starting point — they represent the regulatory-approved status quo that your thesis implicitly argues TFMs should eventually match or exceed. The [[domain-constrained-stacking-2025]] paper is a 2025 example of this lineage still being published in peer-reviewed venues, showing the approach is still actively used and studied.

## See also
[[credit-risk-pd-modeling]], [[domain-constrained-stacking-2025]], [[regulatory-requirements-irb]], [[monotonicity-constraints]]
