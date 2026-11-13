---
title: "Interpretable Credit Scoring via Monotonic Neural Networks"
authors: (per CSBulletin listing, 2025)
year: 2025
venue: Computer Science Bulletin (CSBulletin)
arxiv_id: n/a
tags: [monotonicity, credit-risk, foundational]
---

# MonoNet applied to credit scoring — with counterfactual explanations

A 2025 paper that applies **MonoNet** (the hybrid ante/post-hoc monotonic network from [[mononet-and-terminology-trap]]) directly to credit scoring, combining it with **Counterfactual Explanations** as the interpretability layer. This is exactly the credit-scoring application of Strategy 4's architectural inspiration.

## What they do

Train a MonoNet on credit scoring data — the early layers are unconstrained (flexible representation learning), the final mapping to the credit score is constrained to be monotonic. They then generate counterfactual explanations on top of the MonoNet predictions: "what would this applicant need to change to receive a different credit decision?" Counterfactual explanations are naturally compatible with monotonic models because you can always construct a feasible counterfactual by moving features in the correct monotonic direction.

The paper frames this as solving two regulatory requirements simultaneously: monotonicity (conceptual soundness) and interpretability (ability to explain individual decisions). Counterfactuals answer the practical question applicants and regulators actually ask: "why was this person denied, and what would change it?"

## Why this is both relevant and not a competitor

**Relevant**: Demonstrates that MonoNet's architecture works in credit scoring specifically — which validates the architectural idea behind Strategy 4, and shows you'd have a working implementation template if you pursued it.

**Not a full competitor**: 
- They use a traditional parametric model (MonoNet), not a TFM. The credit-scoring application is well-established territory; your thesis asks whether the same guarantee can be achieved for a pre-trained foundation model.
- They focus on the explanation layer (counterfactuals) more than the PoM cost. No bootstrap-based PoM analysis, no comparison to a GBM baseline.
- The paper appears in a bulletin rather than a top-tier venue, suggesting it's an engineering application rather than a methodological contribution.

## The counterfactual connection — an opportunity

Your bachelor thesis was on Shapley values. Counterfactual explanations and Shapley values are the two dominant individual-level explanation paradigms. A thesis that includes both the PoM analysis (global performance) and a counterfactual or SHAP analysis (individual-level interpretation) would be more complete — and this paper provides precedent for the counterfactual side. If you add a secondary explainability analysis, consider using counterfactuals rather than (or alongside) SHAP for the constrained TabPFN predictions, since counterfactuals are more naturally compatible with monotonic models.

## See also
[[mononet-and-terminology-trap]], [[monotonicity-enforcement-mechanisms]], [[shap-and-monotonicity]], [[credit-risk-pd-modeling]]
