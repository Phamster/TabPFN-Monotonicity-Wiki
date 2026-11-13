---
title: Tabular Foundation Models — Landscape Overview
tags: [concept, tfm, survey]
---

# The TFM Landscape (as of mid-2026)

A fast-moving field — the practical state of the art has shifted multiple times within 2025 alone. Current major lineages:

- **TabPFN family** (Prior Labs / Hollmann, Hutter et al.): [[tabpfn-2023]] → [[tabpfn-v2-2025]] → [[tabpfn-2.5-2025]]. The original and most mature lineage; TabPFN-2.5 is the current strongest performer against XGBoost on small/medium tabular tasks.
- **TabICL family** (Qu, Holzmüller, Varoquaux, Le Morvan): [[tabicl-2025-2026]]. Built explicitly for scale (hundreds of thousands of rows), where TabPFN's context-window limits bite hardest.
- **Mitra** (AutoGluon): diversified synthetic-prior generation, distributed for easy benchmarking — see [[mitra-and-position-paper]].
- A wider ecosystem (Orion-MSP/Orion-Bix, TabDPT, ContextTab, Mothernet, Mitra, LimiX, RealTabPFN, etc.) spanning startups (Prior Labs, NeuralkAI, Layer6 AI, Lexsi Labs) and big tech (Microsoft, AWS, SAP) — most are variations on the same PFN/ICL paradigm with different pretraining priors or scaling tricks.

## What's well-studied vs. not, relative to this thesis

| Dimension | Studied? | Key papers |
|---|---|---|
| Raw predictive accuracy vs. GBDTs | Extensively | [[tabpfn-2.5-2025]], [[tabpfn-3-2026]], [[tabicl-2025-2026]] |
| TFM prediction diversity / ensemble value | New finding: TFMs are near-redundant across architectures | [[tfm-near-redundant-2026]] |
| Context-construction effects | Emerging | [[resampling-credit-risk-tfm-2026]], [[kenfack-fair-icl-2025]] |
| Fine-tuning TFMs | Emerging — mechanical support for Strategy 4 | [[fine-tuning-tfm-2026]] |
| Group/counterfactual fairness | Emerging, TFM-specific work exists | [[fairpfn-2024-2025]], [[kenfack-fair-icl-2025]], [[causal-pretraining-fairness-2026]] |
| Monotonicity / economic consistency | One paper, transport economics only | [[economic-validity-audit-2026]] |
| Monotonicity + credit risk + XGBoost | Studied by Koklev and Alonso-Robisco | [[price-of-monotonicity-credit-pd-2026]], [[alonso-robisco-who-wins-loses-2025]] |
| Monotonicity + credit risk + TFM | **Empty** | — this thesis |
| Regulatory feasibility (CRR/EBA/ECB) | Not studied in any TFM paper | — (see [[regulatory-requirements-irb]]) |

## The near-redundancy finding and what it means for experiment design

[[tfm-near-redundant-2026]] shows that across 153 datasets, six TFMs produce near-redundant predictions — they're architecturally diverse on paper but their outputs are highly correlated. Per-dataset wins: TabPFN v2.5 (52), TabICL v2 (46), others split the rest.

For your thesis this is methodologically useful: you don't need to test all six TFMs to make a general claim about the TFM paradigm. A result on TabPFN-3 (current SOTA, see [[tabpfn-3-2026]]) will approximately generalize. Caveat: near-redundancy in accuracy doesn't imply near-redundancy in monotonicity violation rates — two models with nearly identical AUC could have very different violation patterns. Testing a second TFM (TabICL v2) would let you comment on this directly.

## TabPFN-3 and the scale ceiling shift

[[tabpfn-3-2026]] (May 2026) supports up to 1 million rows and 200 features — the scalability objection that pushed Lending Club and GMSC out of TabPFN's reach no longer applies. If you're running experiments now, use TabPFN-3 rather than earlier checkpoints. This also removes the need to subsample large datasets, eliminating a confound from the earlier experiment design.

## See also
[[prior-fitted-networks]], [[in-context-learning-tabular]], [[credit-risk-pd-modeling]]
