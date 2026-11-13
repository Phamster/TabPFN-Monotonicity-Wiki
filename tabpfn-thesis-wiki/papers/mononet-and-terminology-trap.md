---
title: MonoNet (hybrid ante/post-hoc monotonic networks) — and a terminology trap to avoid
authors: (MonoNet authors per Bioinformatics Advances); Raffel et al. (2017, unrelated "monotonic attention")
year: 2017 / 2023
venue: Bioinformatics Advances / ICML
arxiv_id: n/a / 1704.00784
tags: [monotonicity, foundational]
---

# A hybrid architecture worth borrowing — and a search trap worth flagging

**MonoNet** proposes a compromise between fully ante-hoc constrained architectures (rigid, like Deep Lattice Networks) and purely post-hoc explanation methods: leave the early layers of a network *unconstrained*, so they can learn arbitrary high-level feature representations, but enforce a strict monotonic relationship only between a chosen hidden layer and the final output. The early layers do the flexible representation learning; the late layers carry the interpretability/compliance guarantee. This is a genuinely different design point from anything in [[classical-monotonic-nn-methods]], which mostly constrains the *entire* network end to end.

## Why this matters specifically for transformers/TFMs

MonoNet's split — unconstrained representation learning, then a constrained final mapping — maps unusually well onto a transformer's structure: leave TabPFN's attention layers (where the in-context learning actually happens) completely untouched, and apply a monotonicity constraint **only to the final classification/regression head** that maps the transformer's learned representation to a PD score. This is a fourth candidate enforcement strategy for TFMs, alongside the three identified earlier in this wiki (prior modification, context engineering, post-hoc adapter) — see the full comparison in [[monotonicity-enforcement-mechanisms]]. As far as this literature pass can tell, nobody has proposed or tested a MonoNet-style "constrain only the output head" approach specifically for a PFN/TFM architecture.

## Terminology trap: "monotonic attention" is a different concept entirely

A search for "monotonic transformer" or "monotonic attention" turns up a substantial, unrelated literature (Raffel et al. 2017 and many follow-ups) about **sequence-to-sequence alignment monotonicity** — the constraint that an output token's attention should move forward through the input sequence in order, used in speech recognition and simultaneous translation to enable online/linear-time decoding. This has nothing to do with feature-output monotonicity (the credit-risk sense used throughout this wiki) — it's about the *order* in which a decoder attends to input positions, not about whether increasing a feature's value can only move a prediction in one direction. **Flagging this explicitly because it's an easy way to waste search time**: any thesis literature search using the bare term "monotonic attention" or "monotonic transformer" will mostly surface this irrelevant body of work.

## Relevance to thesis
Cite MonoNet as the architectural inspiration for a fourth candidate mechanism; cite the terminology trap note (or just remember it) to keep searches efficient when looking for related work later in the thesis process.

## See also
[[classical-monotonic-nn-methods]], [[monotonicity-enforcement-mechanisms]], [[prior-fitted-networks]]
