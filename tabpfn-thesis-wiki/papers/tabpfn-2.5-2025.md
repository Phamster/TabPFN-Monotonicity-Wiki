---
title: TabPFN-2.5
authors: Grinsztajn, Flöge, Key, Birkel, et al. (Prior Labs)
year: 2025
venue: arXiv (v2 Feb 2026)
arxiv_id: 2511.08667
tags: [tfm, foundational]
---

# TabPFN-2.5 (2025/2026)

The current state-of-the-art TFM release as of mid-2026. Pushes the scale ceiling further (handles datasets up to ~100K samples and ~2K features) and reports very strong head-to-head results against default XGBoost — a 100% win rate on small/medium classification datasets and roughly 87% on larger ones. Also introduces a distillation engine that compresses the transformer into a lightweight MLP or tree ensemble for production deployment, addressing the latency/scalability complaint that has dogged TFMs since the original 2023 paper.

## Relevance to thesis

This is the model you'd actually want to benchmark against XGBoost today — earlier TabPFN versions are already outdated for this purpose given the pace of releases. Two things matter for a regulatory framing: (1) the **distillation step explicitly produces a tree ensemble** as an output artifact, which is interesting because tree ensembles are exactly where the monotonicity-constraint literature ([[monotonicity-constraints]]) already has tooling (e.g., XGBoost's native `monotone_constraints` parameter) — meaning a distilled TabPFN-2.5 might be a more tractable target for constraint-enforcement than the raw transformer; (2) the benchmark numbers are against *vanilla* XGBoost, not constrained/monotonic XGBoost, so the comparison a thesis would need to run (TFM vs. constrained-XGBoost on regulatory criteria, not just accuracy) doesn't exist yet in their reported results.

## See also
[[tabular-foundation-models-landscape]], [[monotonicity-constraints]]
