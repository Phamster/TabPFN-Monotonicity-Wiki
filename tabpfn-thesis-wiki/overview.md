---
title: Overview — Synthesis Across the Three Streams
tags: [synthesis]
---

# Overview

This wiki was seeded in one session to scope a Master's thesis at the intersection of three streams: [[tabular-foundation-models-landscape]], [[counterfactual-fairness]] (and group fairness more broadly), and [[monotonicity-constraints]]. The candidate's background (a bachelor's thesis on Shapley values, working-student experience in risk modeling, an incoming role as risk parameter analyst in project financing) and prior thesis-planning conversation oriented this specifically toward **credit risk / PD modeling under regulatory constraints** — see [[credit-risk-pd-modeling]] and [[regulatory-requirements-irb]].

## The shape of the literature, stream by stream

**TFM landscape**: mature and fast-moving. TabPFN's lineage now beats default XGBoost on most benchmarks ([[tabpfn-2.5-2025]]), and a parallel TabICL lineage targets larger-scale data. This part of the literature is *not* where the gap is — it's well-resourced (Prior Labs, AutoGluon, several startups, big tech labs all publishing).

**Fairness × TFM**: surprisingly developed already. Two genuinely different mechanisms exist — [[fairpfn-2024-2025]]'s prior modification for counterfactual fairness, and [[kenfack-fair-icl-2025]]'s context-selection for group fairness — plus an empirical study ([[causal-pretraining-fairness-2026]]) asking whether vanilla pretraining helps fairness for free. This stream has real depth; a thesis entering here would need to differentiate hard, most plausibly by being the first to test these mechanisms on actual credit/PD data rather than general fairness benchmarks.

**Monotonicity × TFM**: thin. Exactly one line of work ([[economic-validity-audit-2026]] and its 2026 follow-up) directly measures monotonicity violations in a TFM, and it's in transport economics, not credit risk. The classical monotonic-ML toolkit ([[classical-monotonic-nn-methods]]) is mature but has never been connected to the TFM/ICL paradigm — nobody has asked whether constrained architectures, MILP certification, or counterexample-guided training even *make sense* for a model with no gradient-based training step at inference time.

**Credit risk × TFM**: *(corrected 2026-11-11)* now empirically established for accuracy. [[foundation-models-credit-risk-2026]] (Baesens, Lessmann et al.) benchmarks nine TFMs on 14 PD datasets and finds TabPFN-3 best, with a tendency to underpredict default rates. [[resampling-credit-risk-tfm-2026]] covers context strategies. Neither touches fairness or monotonicity. (The June version of this page wrongly called the first paper speculative.)

## Where these streams overlap and where they don't

```
                    TFM Landscape
                   /      |       \
            Fairness   Monotonicity   Credit Risk
              |             |            |
        [well studied]  [1 line of    [2 empirical
        for TFMs        work, wrong   benchmarks (accuracy),
                        domain]       neither touches
                                      fairness/monotonicity]
```

The triple intersection — TFM + (fairness OR monotonicity) + credit risk, tested empirically against actual regulatory criteria — is empty. See [[gap-analysis]] for how to occupy it.

## See also
[[gap-analysis]], [[tabular-foundation-models-landscape]], [[credit-risk-pd-modeling]]
