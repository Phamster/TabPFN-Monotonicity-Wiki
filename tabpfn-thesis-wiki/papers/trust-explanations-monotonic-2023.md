---
title: "Can I Trust the Explanations? Investigating Explainable Machine Learning Methods for Monotonic Models"
authors: (per arXiv listing)
year: 2023
venue: arXiv
arxiv_id: 2309.13246
tags: [monotonicity, credit-risk, regulatory]
---

# Do SHAP values behave differently on monotonically constrained models?

A paper that sits at the exact intersection of monotonicity enforcement and explainability — two of the three pillars of your thesis. The central question: when you impose monotonicity constraints on an ML model, do XAI methods (SHAP specifically) still produce trustworthy explanations? This matters practically because regulatory bodies expect both monotonicity *and* explainable outputs — satisfying one requirement might undermine the other.

## Core argument

Monotonicity constraints change the model's internal structure and decision boundary. SHAP values are computed relative to that structure. If the constrained model is "forced" into certain predictions by the constraint (rather than learning them freely from data), SHAP attributions may reflect the constraint's influence rather than genuine feature contributions from the data. This creates a potential tension: a monotonically constrained model may produce SHAP explanations that are technically accurate (they describe what the model does) but informationally misleading (because what the model does is partly determined by the constraint, not the data).

## Connections in this wiki

This paper provides the analytical bridge between two streams that until now have been kept separate in this wiki:
- [[monotonicity-constraints]] → enforcement mechanisms
- The explainability thread that runs through [[credit-risk-pd-modeling]] and the Alonso-Robisco paper [[alonso-robisco-who-wins-loses-2025]], which uses Shapley regressions to analyze feature importance stability under constraints

## Relevance to thesis

**As a secondary analysis opportunity**: Once you have constrained TabPFN predictions (from Strategy 1 adapter or Strategy 3 context engineering), computing SHAP values on both the constrained and unconstrained versions and comparing them is a natural extension — essentially replicating this paper's methodology on a TFM rather than a traditional model. This would add an explainability dimension to the thesis without requiring a new experiment, just an additional analysis pass on data you already have.

**As a cite-and-differentiate paper**: If a reviewer raises "but does monotonicity break explainability?" you have a direct citation showing this is a known and studied concern, and you can position any SHAP analysis you do as a contribution toward answering it in the TFM context specifically.

**As a framing paper for the regulatory chapter**: Regulatory expectations for IRB models cover both monotonicity *and* explainability (see [[regulatory-requirements-irb]]). A paper showing these two requirements can interact in unexpected ways is useful motivation for why your thesis's multi-criterion evaluation (PoM + any SHAP analysis) is more complete than a simple accuracy benchmark.

## See also
[[monotonicity-constraints]], [[alonso-robisco-who-wins-loses-2025]], [[regulatory-requirements-irb]], [[shap-and-monotonicity]]
