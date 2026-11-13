---
title: "Monotonic Neural Additive Models: Pursuing Regulated Machine Learning Models for Credit Scoring"
authors: Chen, Dangxing; Ye, Weicheng
year: 2022
venue: ACM International Conference on AI in Finance (ICAIF 2022)
arxiv_id: 2209.10070
tags: [monotonicity, credit-risk, regulatory, foundational]
---

# Monotonic NAMs for credit scoring — the closest published architectural competitor to Strategy 4

A 2022 ACM paper that independently arrives at the same regulatory framing your thesis builds on: "In the absence of compliance with regulatory requirements, even highly accurate machine learning methods are unlikely to be accepted for credit scoring." Their solution is a **Monotonic Neural Additive Model (MNAM)** — a neural network architecture that simultaneously achieves higher accuracy than logistic regression and full monotonicity guarantee, by restricting the architecture to be monotonic by construction rather than by post-hoc enforcement.

## What Neural Additive Models are

A NAM decomposes the prediction into a sum of learned functions of individual features: `f(x) = f1(x1) + f2(x2) + ... + fk(xk)`. Each `fi` is a small neural network. This gives both flexibility (each sub-network can learn any non-linear shape) and interpretability (you can plot each `fi` separately and see exactly what the model learned for that feature). Making the NAM *monotonic* means constraining each `fi` so it can only increase (or only decrease) with its input — this is straightforward since `fi` is a single-input network and standard monotonic activation tricks (positive weights, cumulative sum architectures) apply cleanly.

The connection to [[monotonicity-enforcement-mechanisms]] Strategy 4 (output-head constraint, MonoNet-style): MNAM is an extreme version of that idea — the entire network is monotonic by construction, not just the final mapping. This is more constrained than what Strategy 4 proposes (which only constrains the head while leaving the representation layers free), so MNAM is actually *less* flexible but *more* provably monotonic.

## Follow-up paper worth tracking

The same authors extended this work in a 2023 ICML paper: *"How to Address Monotonicity for Model Risk Management?"* — which appears in several related-paper citation lists. This follow-up presumably engages more directly with the model risk management / regulatory framing that the 2022 paper introduces. Track down and read this before writing the methodology chapter, as it may have evolved the approach in ways that affect how you position Strategy 4.

## Relevance to thesis

**Why this is a competitor**: If a practitioner wants a monotonic neural model for credit scoring, Chen & Ye (2022) already offers one that works and has been published. This weakens the motivation for Strategy 4 (output-head constraint on TabPFN) slightly — you'd need to argue why a TabPFN with a constrained head is better than just using a MNAM, which isn't obvious unless TabPFN's accuracy advantage survives the head constraint (which is empirically untested).

**Why it's not a full competitor**: MNAM has no in-context learning, no foundation model properties, and is trained from scratch per dataset. The question Strategy 4 addresses is whether a pre-trained tabular foundation model can have monotonicity built in at the output-head level while retaining the accuracy advantage that comes from pretraining — which MNAM cannot test, because it has no pretraining. The positioning is: MNAM solves monotonicity for traditional neural networks; your thesis tests whether the same architectural trick applies to TFMs.

**The most important distinction**: MNAM enforces monotonicity at training time for a dataset-specific model. Strategies 1 and 3 in your thesis (adapter and context engineering) enforce it at inference time for a pre-trained model that never gradient-trains on your data. This is a fundamentally different paradigm, not a minor variation.

## See also
[[classical-monotonic-nn-methods]], [[monotonicity-enforcement-mechanisms]], [[mononet-and-terminology-trap]], [[credit-risk-pd-modeling]]
