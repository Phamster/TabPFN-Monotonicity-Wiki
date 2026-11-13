---
title: "Decomposing the Price of Monotonicity Constraints with Shapley Values in Credit Scoring"
authors: Alonso-Robisco, Andres; Carbó, José Manuel; De Haro Rodríguez, Guillermo; Garcia Guillen, Juan Jose
year: 2026 (replication package 5 Nov 2026; manuscript not yet located)
venue: manuscript; replication package on Zenodo (DOI 10.5281/zenodo.23982617)
arxiv_id: n/a
tags: [monotonicity, credit-risk, regulatory]
---

# Which constraints cause the Price of Monotonicity?

Found in the 2026-11-11 gap-watch search. So far only the Zenodo replication package is public; it names the manuscript and its supplement but gives no arXiv or journal link. Find the manuscript before citing it.

## What it does

Each monotonicity constraint on a credit scoring model is treated as a player in a cooperative game. The value function retrains the model under every subset of constraints. The Shapley value then splits the total accuracy cost of the full constraint set across the individual constraints. The same retrained models trace a cost frontier that helps decide which constraints to keep.

- Model: XGBoost (3.2.0) only. No tabular foundation models.
- Data: German Credit, Taiwan Credit and Polish Bankruptcy (all UCI), which overlap with your datasets.
- Authors: the Bank of Spain / IE / UPM group behind [[alonso-robisco-who-wins-loses-2025]].

## Relevance to thesis

1. **Not a competitor on the core question.** It stays within GBMs, like [[price-of-monotonicity-credit-pd-2026]]. Your TFM question is still open.
2. **But it raises the bar on the GBM side.** Reviewers may now expect the PoM to be broken down per constraint, not just reported in total.
3. **Natural extension that fits your background** (bachelor thesis on Shapley values): run the same per-constraint decomposition for TabPFN with the adapter (Strategy 1), and compare which constraints are expensive for a TFM vs. for XGBoost. Cost note: the value function retrains under every subset, so with k constraints you need 2^k fits per dataset. That is cheap for the adapter (only Stage 1 changes, the TFM prediction is computed once) but expensive for anything that reruns the TFM.
4. Strong candidate for an optional analysis in Phase 2, or a discussion point with Lessmann.

## See also
[[price-of-monotonicity-credit-pd-2026]], [[alonso-robisco-who-wins-loses-2025]], [[shap-and-monotonicity]], [[monotonicity-enforcement-mechanisms]]
