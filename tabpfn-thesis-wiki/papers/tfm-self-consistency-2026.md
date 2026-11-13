---
title: "Do Tabular Foundation Models Agree with Themselves?"
authors: (per arXiv; verify)
year: 2026
venue: arXiv
arxiv_id: 2608.06004
tags: [tfm]
---

# Behavioural consistency is a separate axis from accuracy

Found in the 2026-11-11 gap-watch search. Supporting citation only.

## What it does

Tests whether TFMs give probabilistically consistent answers when the roles of features and targets are swapped or marginalised. Every tested model violates both consistency conditions on every dataset. The newest model (TabFM) comes closest, but consistency does not correlate strongly with accuracy, so the authors argue it is a distinct axis that benchmarks like TabArena do not capture.

## Relevance to thesis

- General support for your premise: high benchmark accuracy says nothing about whether a TFM behaves sensibly, so behavioural audits (like your monotonicity violation rate) are needed separately.
- Pairs well with [[economic-validity-audit-2026]] in the introduction: two independent findings that TFMs fail structural checks they were never trained for.

## See also
[[economic-validity-audit-2026]], [[tabular-foundation-models-landscape]], [[monotonicity-constraints]]
