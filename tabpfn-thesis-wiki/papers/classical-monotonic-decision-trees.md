---
title: Classical monotonic decision trees, and a partially-monotonic discrete choice model
authors: Potharst & Feelders (2002); Velikova & Daniels (2004); Hu et al. (2012); Marsala & Petturiti (2015); Pei et al. (2016); Kim & Bansal (2024)
year: 2002-2024
venue: various
arxiv_id: n/a (mixed venues)
tags: [monotonicity, foundational]
---

# Monotonic decision trees, and a hybrid econometric-ML answer to the same problem

A second classical thread, distinct from the monotonic *neural network* literature in [[classical-monotonic-nn-methods]]: a sequence of papers (2002-2016) on building **monotonic decision trees** by altering the tree-growing/splitting process itself so that monotonicity constraints are never violated, rather than bolting constraints onto an already-built model. Conceptually this is the direct ancestor of XGBoost/LightGBM/CatBoost's native `monotone_constraints` parameters (which restrict split selection during tree growth to only consider splits compatible with the declared monotonic direction) — see [[price-of-monotonicity-credit-pd-2026]] for the modern, quantified version of exactly this idea applied to credit PD.

**Kim & Bansal (2024)**, in transport economics, takes a related but architecturally different approach worth knowing about: a **partially monotonic discrete choice model** that enforces monotonicity of the modeled utility only with respect to a *specified subset* of attributes (e.g., cost, time), while still allowing flexible, non-linear, ML-style learning for the remaining attributes. This is conceptually a middle ground between a fully-constrained econometric model (rigid, but interpretable) and an unconstrained ML model (flexible, but unpredictable) — partial rather than global monotonicity.

## Relevance to thesis

Two distinct, useful ideas for a TFM-monotonicity methodology section:

1. **Constrained split selection** (the decision-tree lineage) is the *mechanism* underneath every native GBM monotonicity implementation benchmarked in [[price-of-monotonicity-credit-pd-2026]] — useful to cite when explaining *how* the GBM baseline actually achieves its guarantee, as distinct from the TFM side where no equivalent "split selection" step exists to constrain (TFMs don't grow trees; they do a single forward pass over an attention mechanism). This is precisely the structural mismatch noted in [[monotonicity-enforcement-mechanisms]] — credit risk's most mature constraint-enforcement tooling is mechanically tied to tree structure, which TFMs don't have.
2. **Partial monotonicity** (Kim & Bansal) is directly relevant to credit risk's actual regulatory practice: EBA/ECB guidance doesn't require *every* risk driver to be monotonic — only the ones where domain knowledge dictates a clear direction (debt ratios, delinquency history) — while others (categorical industry codes, geography) reasonably have no such requirement. A thesis methodology should specify *which* features get a monotonicity constraint and which don't, exactly as Koklev's benchmark already does and as Kim & Bansal's architecture explicitly supports — this is the "partial, not global" framing worth adopting rather than naively forcing every feature to be monotonic.

## See also
[[classical-monotonic-nn-methods]], [[price-of-monotonicity-credit-pd-2026]], [[monotonicity-enforcement-mechanisms]]
