---
title: Mitra (AutoGluon) and the "TFMs should be a research priority" position paper
authors: Zhang et al. (Mitra); van Breugel & van der Schaar (position paper)
year: 2025 / 2024
venue: NeurIPS / ICML position track
arxiv_id: n/a
tags: [tfm, foundational, survey]
---

# Mitra & the case for tabular foundation models

**Mitra** is AutoGluon's entry into the TFM space, using "mixed synthetic priors" — i.e., diversifying the synthetic pretraining data generation process beyond the single-SCM-family approach TabPFN uses. Distributed via AutoGluon and Hugging Face, making it one of the more accessible TFMs for quick benchmarking without committing to the TabPFN/Prior Labs ecosystem specifically.

**van Breugel & van der Schaar (2024)** is a position paper, not an empirical one — it argues TFMs deserve dedicated research investment, identifying open challenges like cross-dataset generalization and handling tables with mixed numeric/string types. It's a useful citation for *framing* why this is a legitimate research area, separate from any specific empirical claim.

## Relevance to thesis

Mitra matters because it's one of the two models tested in the [[monotonicity-constraints]]-relevant discrete-choice audit paper (alongside TabPFN v2) — meaning there's already a documented monotonicity failure case for this exact model, just not in a credit context. The position paper is good for the introduction/motivation section of a thesis: it establishes that the field itself considers TFM evaluation an open and worthwhile problem, which supports a thesis on regulatory feasibility rather than pure benchmarking.

## See also
[[tabular-foundation-models-landscape]], [[monotonicity-constraints]]
