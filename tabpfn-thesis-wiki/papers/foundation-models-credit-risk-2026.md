---
title: "Tabular Foundation Models for Credit Risk Prediction: A Dedicated Review and Empirical Comparison (v1/v2 title: Foundation Models for Credit Risk Prediction: A Game Changer?)"
authors: Baesens, Goethals, Lessmann, De Vos, Bravo, Martens, Medina-Olivares, Mues, Oskarsdóttir, vanden Broucke, Van Gestel, Verdonck, Verbeke
year: 2026 (v1 18 May 2026, v2 15 Jul 2026, v3 23 Oct 2026)
venue: arXiv (invited review)
arxiv_id: 2605.18147
tags: [tfm, credit-risk, regulatory]
---

# The closest existing competitor — and your supervisor is a co-author

> **Supersession note (2026-11-11):** the June 2026 version of this page called the paper "speculative, tests nothing". That was wrong; it was written from search snippets of v1. The paper is a large empirical benchmark (already in v1, much expanded in v3). Everything below replaces the old description. Stefan Lessmann is the third author.

## What it does

A benchmark of tabular foundation models against classical and advanced ML for the two core Basel risk parameters: PD (classification) and LGD (regression). All TFMs are used out of the box, without tuning.

- **PD:** 9 TFMs (TabPFN, TabPFNv2, TabPFN-2.5, TabPFN-3, Real-TabPFN, TabICL, TabICLv2, TabDPT, Mitra) on 14 datasets. Public ones include German Credit, Give Me Some Credit, LendingClub, Taiwan Credit Card, HMEQ, Home Credit and Thomas; two are proprietary.
- **LGD:** 6 TFMs on 7 datasets (Freddie Mac, LendingClub, five proprietary).
- Five-fold cross-validation; competitors include CatBoost, LightGBM, XGBoost and many deep tabular models.
- Metrics: AUC as primary, plus Brier, log loss, KS and others; calibration checked as observed vs. mean predicted default rate.

## Main findings (v3)

- TabPFN-3 has the best average performance on both PD and LGD.
- PD mean AUC: TabPFN-3 0.764, TabICLv2 0.760, TabPFN-2.5 0.757, TabICL 0.753; best conventional learner CatBoost 0.750. The LGD gap in favour of TabPFN-3 is larger (R² 0.537 vs. 0.487).
- The original TabPFN and Mitra are among the weakest PD learners, so older checkpoints should not stand in for "the TFM".
- **Calibration:** TFMs tend to *underpredict* default rates. TabPFN-3 underpredicts in all 14 PD datasets (mean bias about 1.4 pp); CatBoost leans the other way. The authors flag this as more serious for internal rating models than for approval scorecards.
- The TFM advantage is largest at small-to-moderate sample sizes and under strong class imbalance.
- Regulation (EU AI Act, GDPR, Basel IRB, IFRS 9) and XAI appear in the review part, but **the paper does not evaluate explainability and does not test monotonicity** (checked in the v3 HTML on 2026-11-11; only part of the text was readable, so re-check future-research section 6.2 in the PDF).

## Relevance to thesis

1. **It settles the accuracy premise.** You no longer need to argue that TFMs might be competitive for PD: your supervisor's group showed TabPFN-3 is the top PD model across 14 datasets. Your thesis asks the next question: does that advantage survive the monotonicity constraints regulators expect?
2. **Dataset overlap** with your setup (German, GMSC, LendingClub, Taiwan) lets you sanity-check your unconstrained TabPFN-3 AUCs against theirs.
3. **The calibration finding matters for Brier-PoM** (see [[calibration-vs-discrimination]]): TabPFN-3 already underpredicts PD, so check whether the adapter (Strategy 1) fixes or worsens that bias.
4. **Positioning changes:** the old line "they speculate, we test" is gone. New line: they benchmark accuracy and calibration; we test regulatory monotonicity and its price. See [[thesis-positioning]].
5. Ask Lessmann early whether section 6.2 already lists monotonicity or constraint compliance as future work, and whether his group plans a follow-up.

## See also
[[credit-risk-pd-modeling]], [[regulatory-requirements-irb]], [[tabular-foundation-models-landscape]], [[tabpfn-3-2026]], [[resampling-credit-risk-tfm-2026]], [[thesis-positioning]]
