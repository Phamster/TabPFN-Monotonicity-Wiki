---
title: "A Mathematical Certification for Positivity Conditions in Neural Networks with Applications to Partial Monotonicity and Trustworthy AI"
authors: (per arXiv listing)
year: 2024
venue: arXiv
arxiv_id: 2406.08525
tags: [monotonicity, regulatory, foundational]
---

# Mathematical certification of partial monotonicity — and an explicit EBA/CRR connection

A 2024 paper that sits at the intersection of formal verification, neural network monotonicity, and financial regulation. Crucially, it explicitly cites both the **EBA follow-up report on machine learning for IRB models (2023)** and the **Capital Requirements Regulation (CRR)** as motivation — making it one of the few ML papers that directly engages with the regulatory text your thesis needs to address, rather than gesturing at "regulatory requirements" abstractly.

## What it does technically

Develops a mathematical framework for **certifying** that a neural network satisfies positivity or partial monotonicity conditions — meaning: given a trained network, you can prove formally (not just empirically check) that it satisfies the constraint over the full input space, not just the training/test sample. The technique involves analyzing the network's Lipschitz structure and activation functions to derive certificates.

This is the verification side of monotonicity enforcement, complementing the enforcement mechanisms in [[monotonicity-enforcement-mechanisms]]:
- Enforcement (your thesis) asks: how do you make the model monotonic?
- Certification (this paper) asks: how do you prove it is monotonic?
Both matter for regulatory approval — enforcement gives you the model, certification gives you the audit trail a regulator can inspect.

## The partial monotonicity framing

The paper addresses **partial monotonicity** — monotonicity with respect to a subset of features, not all of them. This is exactly the realistic credit risk setting: you declare 6 of 20 features monotonic (the economically sensible ones) and leave the rest unconstrained. The certification question then becomes: prove the network is monotonic in those 6 directions while allowing arbitrary behavior in the other 14.

This connects directly to [[classical-monotonic-decision-trees]]'s Kim & Bansal partial monotonicity framing and to the practical constraint specification you implement in `src/datasets.py` — the `mono_map` dictionary is exactly a partial monotonicity specification.

## Why this paper matters for the thesis even if you don't implement certification

The regulatory gap it identifies is useful for your motivation section: current TFM deployments have no certification mechanism — you can empirically measure the PoM and violation rate, but you cannot *prove* the model will be monotonic on any new input not in the test set. This is a known limitation of all post-hoc enforcement approaches (including your Strategy 1 adapter), and this paper is the citation for that limitation.

## The EBA/CRR connection in print

The paper cites:
- EBA, "Machine Learning for IRB Models," September 2023 (the follow-up report confirming ML is being evaluated for IRB use)
- CRR Capital Requirements Regulation EBA interactive single rulebook

These citations appear alongside the paper's formal results, creating a direct textual bridge between mathematical certification theory and the specific regulatory documents your [[regulatory-requirements-irb]] concept page summarizes. This is useful because it demonstrates to a thesis reader that the formal verification community already sees the EBA/CRR as the relevant regulatory anchor — supporting your choice to use the same anchor.

## See also
[[regulatory-requirements-irb]], [[monotonicity-enforcement-mechanisms]], [[monotonicity-constraints]], [[chen-ye-monotonicity-mrm-2023]]
