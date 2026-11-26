---
title: Stop explaining black box machine learning models for high stakes decisions and use interpretable models instead
authors: Rudin
year: 2019
venue: Nature Machine Intelligence 1(5):206–215
doi: 10.1038/s42256-019-0048-x
arxiv_id: 1811.10154
tags: [interpretability, regulation, position]
---

# Rudin (2019): interpretable by design

Checked 2026-11-26 via Crossref and arXiv. Thesis bib key `rudin2019stop`.

Argues that explaining black boxes after the fact in high-stakes decisions perpetuates bad practice and can
cause harm; explanations are approximations that may be wrong where it matters. Inherently interpretable
models should be used instead, and they often lose little or no accuracy. Examples from criminal justice,
healthcare and computer vision; credit scoring is one of the high-stakes settings named.

## Relevance to thesis
- The normative argument for **enforcing** monotonicity rather than measuring or explaining it afterwards.
  Fits the ECB guide's expectations (para 60–62, [[regulatory-requirements-irb]]): complexity must be
  justified by performance, and estimates must be plausible and intuitive.
- The PoM is exactly Rudin's empirical question for TabPFN: how much accuracy does the constrained,
  more interpretable version lose? Small PoM = her "little loss" claim holds here too.
- Use in Ch. 1 (motivation) and Ch. 7 (adapter/distillation vs. raw TabPFN + SHAP).

## See also
[[shap-and-monotonicity]], [[dumitrescu-pltr-2022]], [[thesis-positioning]]
