---
title: "Constrained Machine Learning Models for Credit Default Prediction: Who Wins, and Who Loses?"
authors: Alonso-Robisco, Andres; Carbo, Jose Manuel; de Haro, Guillermo; Guillén García, Juan José
year: 2025
venue: EUI Robert Schuman Centre Working Paper (RSC 2025/24)
arxiv_id: n/a (cadmus.eui.eu)
tags: [monotonicity, credit-risk, fairness, regulatory]
---

# Who wins and who loses under monotonicity constraints in credit PD

**Critical paper to differentiate from — read in full before writing the literature review chapter.** This is the closest published work to the XGBoost portion of your thesis, and Koklev already cites it as directly related. Published by the European University Institute's Florence School of Banking and Finance, so it will be on any reviewer's radar.

## What they do

Constrained vs. unconstrained XGBoost on **Lending Club** data (one dataset, not a multi-dataset benchmark). Their distinct contribution: after measuring the predictive performance impact of constraints, they identify *which individuals* are most affected — whose PD scores change the most when constraints are imposed — and test whether feature importances change significantly under constraints using **Shapley regressions** (the Joseph 2019/2024 statistical framework, which tests SHAP value significance rather than just reporting point estimates). This allows them to evaluate "not only what variables drive the model's predictions, but also how consistently and reliably they do so under monotonicity constraints."

## What they find (from abstract)

Monotonicity constraints affect predictive performance but the impact is unequal across borrowers — certain individuals' predicted PDs shift substantially while others are barely affected. The Shapley regression analysis provides statistical evidence on which features retain informational value under constraints. They also connect findings to potential fairness implications, since constrained models may shift default probabilities in ways that disproportionately affect certain demographic groups.

## How this differs from your thesis

The distinctions matter and need to be stated explicitly in your literature review:

1. **Model scope**: They use XGBoost only. Your thesis asks the same PoM question for a model family (TFMs) where no existing answer exists.
2. **Metric**: They don't use the paired-bootstrap PoM metric. Their performance analysis is simpler; their main contribution is the Shapley regression analysis of *whose scores change*, not *how much AUC is lost*.
3. **Scale**: One dataset (Lending Club). Koklev covers five, your thesis extends to the corrected South German Credit as well.
4. **Research question**: They ask "who is affected by constraints?" Your question is "what does enforcing constraints cost a TFM, and which enforcement mechanism minimizes that cost?" Completely different questions using the same general setup.

The positioning sentence you need in your thesis: *"Alonso-Robisco et al. (2025) investigate the distributional consequences of monotonicity constraints — who is affected and how feature importances shift. Our work addresses a prior, more fundamental question: whether such constraints can be enforced on tabular foundation models at all, and at what accuracy cost."*

## Unexpected opportunity

Their finding that certain individuals are disproportionately affected by constraints is a natural *secondary analysis* to add to your thesis almost for free — once you have TabPFN's constrained vs. unconstrained PD scores, you can run the same distributional analysis they run (which borrowers shift most) and compare whether the pattern differs between a TFM and XGBoost under the same constraints. That would be a genuine addition to their paper, not just a replication.

## Follow-up from the same group (added 2026-11-11)

The same four authors released a replication package (Zenodo, 5 Nov 2026) for a new manuscript that decomposes the Price of Monotonicity per constraint with Shapley values. See [[shapley-pom-decomposition-2026]].

## See also
[[price-of-monotonicity-credit-pd-2026]], [[shapley-pom-decomposition-2026]], [[monotonicity-constraints]], [[credit-risk-pd-modeling]], [[shap-and-monotonicity]]
