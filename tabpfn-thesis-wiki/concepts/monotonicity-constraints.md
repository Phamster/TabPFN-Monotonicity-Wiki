---
title: Monotonicity Constraints in ML
tags: [concept, monotonicity, regulatory]
---

# Monotonicity Constraints

A model is monotonic with respect to a feature if increasing that feature's value can only move the prediction in one consistent direction (never the other), holding other features fixed. In credit risk, this is a hard requirement, not a preference: regulators expect that, e.g., increasing leverage cannot *decrease* a borrower's modeled PD, and EBA/ECB guidelines on PD/LGD estimation expect risk drivers to behave in economically sensible, monotonic ways (see [[regulatory-requirements-irb]]).

## Two completely separate literatures that are now starting to meet

**Classical ML monotonicity** ([[classical-monotonic-nn-methods]], [[classical-monotonic-decision-trees]]) is mature: constrained architectures (Deep Lattice Networks), post-hoc certification via MILP, counterexample-guided retraining (COMET), monotonic decision trees, and newer expressive-yet-constrained activation designs. XGBoost and LightGBM also ship native `monotone_constraints` parameters — and as of [[price-of-monotonicity-credit-pd-2026]], the *cost* of using them in credit PD specifically is now rigorously quantified (a "Price of Monotonicity" of roughly 0-2.9% AUC, depending on dataset size and constraint coverage) across three GBM libraries and five public credit datasets. This is genuinely solved territory for tree ensembles.

**TFM monotonicity** is still thin, but no longer a single data point. [[economic-validity-audit-2026]] finds TabPFN v2 and Mitra violate monotonicity on roughly half of test cases in a transport-economics discrete-choice setting, and demonstrates a working two-stage adapter fix. No equivalent study exists for credit risk yet — meaning the natural next step is running [[price-of-monotonicity-credit-pd-2026]]'s exact benchmark logic on a TFM equipped with an enforcement mechanism, to get a directly comparable "Price of Monotonicity for TFMs" number.

## Candidate enforcement strategies for TFMs

Four distinct mechanisms have been identified, none tested in a credit-risk setting — see [[monotonicity-enforcement-mechanisms]] for the full technical breakdown, comparison table, and effort/evidence assessment of each: (1) a post-hoc adapter wrapping a constrained structural model around the TFM's output, (2) prior modification analogous to FairPFN's approach for fairness, (3) context engineering analogous to Kenfack et al.'s approach for fairness, and (4) a MonoNet-style constraint applied only to the TFM's final output head.

## See also
[[monotonicity-enforcement-mechanisms]], [[economic-validity-audit-2026]], [[price-of-monotonicity-credit-pd-2026]], [[classical-monotonic-nn-methods]], [[classical-monotonic-decision-trees]], [[regulatory-requirements-irb]], [[prior-fitted-networks]]
