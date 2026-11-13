---
title: SHAP Values Under Monotonicity Constraints
tags: [concept, monotonicity, credit-risk]
---

# SHAP Values Under Monotonicity Constraints

A cross-paper synthesis that didn't have its own concept page but recurs across at least three papers in this wiki — worth consolidating since any explainability analysis in the thesis needs to engage with this cleanly.

## The core tension

SHAP values decompose a model's prediction into additive feature contributions. They describe what the model *does*, not what the data *says*. When a monotonicity constraint is imposed on a model, the model is partly doing what the data says and partly doing what the constraint requires. SHAP cannot distinguish these two sources — it attributes the prediction to features regardless of why the model behaved as it did.

This creates a specific problem in credit risk: a constrained model might assign a very high PD to a borrower partly because their leverage is genuinely high (data-driven) and partly because the constraint forces PD to be high whenever leverage exceeds a threshold (constraint-driven). SHAP would distribute credit for this high PD prediction across all features, making the constraint's contribution look like a data-driven feature importance signal.

## What the papers say

**[[trust-explanations-monotonic-2023]]** raises this concern directly and investigates whether XAI methods remain trustworthy on constrained models. The finding (from the abstract/title framing) suggests the interaction is non-trivial and worth testing explicitly.

**[[alonso-robisco-who-wins-loses-2025]]** uses Shapley regressions (not standard SHAP, but a statistical test of SHAP value significance via the Joseph framework) to ask whether feature importances change under constraints. Their finding that importances *do* shift provides empirical evidence that constraints interact with SHAP in ways that matter for interpretation.

**The Lessmann XAI for OR paper** (background paper, see [[credit-risk-pd-modeling]]) establishes the general need for faithful XAI in operational research contexts — faithfulness is precisely the property at risk when constraints interact with SHAP.

## What this means for the thesis

If your thesis includes any SHAP analysis alongside the PoM metric — which is a natural addition given your Shapley background from your bachelor thesis — you need to be explicit that:
1. SHAP values on constrained models describe the constrained model's behavior, not the unconstrained data-generating process
2. Changes in SHAP values between constrained and unconstrained models reflect both the constraint's direct effect and any indirect effects on learned feature relationships
3. This is a known limitation (cite [[trust-explanations-monotonic-2023]]) and an argument for presenting both constrained and unconstrained SHAP side by side rather than treating either as ground truth

An alternatively framed secondary contribution: test whether SHAP values on the Strategy 1 adapter (sign-constrained LR + TabPFN correction) are more faithful/stable than SHAP values on raw TabPFN, since the adapter's structure explicitly separates the constraint-driven component (Stage 1) from the data-driven component (Stage 2). This decomposition might actually produce more interpretable SHAP values, not less.

## Practical note: TreeSHAP vs. KernelSHAP

For XGBoost: TreeSHAP is exact and fast — use it. For TabPFN: only KernelSHAP is available (it's a transformer, not a tree), which is approximate and slow. This is a practical constraint on how many SHAP explanations you can compute for the TFM experiments.

## See also
[[trust-explanations-monotonic-2023]], [[alonso-robisco-who-wins-loses-2025]], [[monotonicity-constraints]], [[monotonicity-enforcement-mechanisms]]
