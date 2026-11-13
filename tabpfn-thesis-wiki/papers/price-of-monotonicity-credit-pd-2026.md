---
title: "What's the Price of Monotonicity? A Multi-Dataset Benchmark of Monotone-Constrained Gradient Boosting for Credit PD"
authors: Koklev, Petr
year: 2025 (v1 Dec 2025) / 2026 (v2 Mar 2026)
venue: arXiv
arxiv_id: 2512.17945
tags: [monotonicity, credit-risk, regulatory]
---

# The exact GBM-side baseline this thesis needs — and a sharpening of the gap

**Found while going deeper on monotonicity-enforcement mechanisms — this paper changes the gap-analysis framing materially (see [[gap-analysis]]).** An independent researcher (PhD in Economics) runs exactly the benchmark a thesis would otherwise have had to build from scratch as a baseline: monotone-constrained vs. unconstrained gradient boosting (XGBoost, LightGBM, CatBoost — all three libraries' native `monotone_constraints` implementations) for credit PD, across **five public datasets** spanning consumer credit, corporate bankruptcy, and peer-to-peer lending contexts (German Credit is confirmed among them from a categorical-feature-handling discussion in the paper; the others need verifying against the primary source before citing).

**The core contribution**: a formally defined metric, the **Price of Monotonicity (PoM)** — the relative change in a standard performance metric (AUC) when moving from an unconstrained to a monotone-constrained model, estimated via paired bootstrap comparisons rather than a single point estimate. Empirically: PoM in AUC ranges from essentially zero (often statistically indistinguishable from zero) on large datasets, up to roughly 2.9% on smaller datasets with extensive constraint coverage (many features constrained at once). The headline conclusion: appropriately specified monotonicity constraints are nearly free on large-scale credit portfolios and only meaningfully costly when data is scarce and many features are constrained simultaneously.

The paper explicitly notes (as motivation) that despite monotonicity constraints being widely available in all major GBM libraries, no prior work had systematically quantified their cost across multiple datasets and implementations for credit PD specifically — and that the literature offers limited empirical guidance on how to even specify which features should be constrained in which direction, beyond general domain-knowledge principles (e.g., higher delinquency should imply higher PD).

## Relevance to thesis — this is a bigger deal than it first looks

This paper **answers, for gradient boosting, almost exactly the question a TFM-monotonicity thesis would otherwise be the first to ask** — just for the wrong model family. That's good news, not bad news, for two reasons:

1. **It hands you a ready-made, methodologically rigorous baseline.** Instead of inventing a "Price of Monotonicity"-style metric from scratch, a thesis can directly adopt Koklev's PoM definition and bootstrap methodology, then ask the *parallel* question for TFMs: what is the Price of Monotonicity when using a TFM-based enforcement mechanism (the post-hoc adapter from [[economic-validity-audit-2026]], or a [[monotonicity-enforcement-mechanisms]]-style alternative) instead of native GBM constraints? This converts a vague "explore the gap" thesis into a precisely comparable, replicable study design — same metric, same logic, different model family.
2. **It sharpens exactly where the remaining gap is.** The gap is no longer "is monotonicity costly in credit PD" (now answered, for GBMs: usually cheap, sometimes ~3% AUC on small/constrained portfolios) — it's specifically: **does the Price of Monotonicity for TFMs match, exceed, or fall below the GBM-established baseline, and does the answer depend on dataset size the same way it does for GBMs?** If TFM context-window size constraints (TabPFN v2 tops out around 10K samples) interact with the "small data = costlier monotonicity" finding here, that would be a genuinely new and practically important result, since it's exactly TFMs' selling point (strong performance on small data) running headlong into exactly where Koklev finds monotonicity is most expensive.
3. If feasible, reusing one or more of Koklev's five datasets directly would let a thesis report PoM numbers that are *directly comparable* to a peer-reviewed-adjacent baseline, rather than needing to justify a new dataset choice from scratch.

## See also
[[economic-validity-audit-2026]], [[monotonicity-enforcement-mechanisms]], [[credit-risk-pd-modeling]], [[regulatory-requirements-irb]]
