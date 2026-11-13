---
title: Auditing and Fixing Economic Validity in Tabular Foundation Models for Discrete Choice
authors: Wang, Yingshuo; Sun, Xian; Li, Yanhang; Fan, Zhichao; Zhuang, Zexin
year: 2026
venue: ICML 2026 Workshop on Foundation Models for Structured Data (FMSD); full-length follow-up arXiv:2606.26432
arxiv_id: 2605.26559
tags: [tfm, monotonicity]
---

# The closest existing proof that TFMs violate monotonicity — just not in credit risk

**This is the single most important paper in this wiki for the thesis gap.** It audits two TFMs (Mitra and TabPFN v2) on discrete-choice modeling tasks from transport economics (predicting travel-mode choice — car, train, bus — as a function of cost, time, etc.). Discrete choice models have long-standing economic-consistency requirements analogous to credit risk's regulatory monotonicity requirements: e.g., raising the cost of an option should never increase the probability of choosing it.

The finding: raw TFM predictions (tested for both Mitra and TabPFN v2) achieve meaningfully higher accuracy than a classical multinomial logit (MNL) baseline — 14 percentage points higher on the Swissmetro dataset, 4.4 points on the London Passenger Mode Choice (LPMC) dataset — but at a real cost. The MNL baseline, by construction, satisfies monotonicity 100% of the time and produces economically sensible willingness-to-pay estimates consistent with published benchmarks; the raw TFMs satisfy monotonicity for only around half of test observations on the harder dataset, meaning for roughly half the cases the model implies that raising a price would *increase* the probability of choosing that option.

**The fix, in technical detail** — this is the part worth adapting for credit risk: a *two-stage adapter* that doesn't touch the TFM at all.
- **Stage 1**: fit a standard econometric choice model (the MNL) whose coefficients are explicitly sign-constrained to respect economic theory (e.g., the cost coefficient must be negative). This stage is trained *without* any TFM input, so the resulting structural parameters are guaranteed monotonic by construction and are completely unaffected by which TFM (or whether any TFM) is used downstream.
- **Stage 2**: freeze those Stage-1 parameters, then train a separate correction term that takes the frozen MNL output plus the raw TFM's prediction as additional information, and learns how much to nudge the MNL prediction using what the TFM picked up that the MNL structure couldn't capture.
- **Result**: the combined Adapter+TFM model recovers 13 of the 14 accuracy points lost by the pure MNL on Swissmetro (reaching the same 76.6% accuracy regardless of whether Mitra or TabPFN v2 supplies the correction signal), while maintaining 100% monotonicity and economically sensible willingness-to-pay estimates — essentially the same as the unconstrained MNL's, confirming the TFM's predictions never get to override the protected economic structure, only to refine it within the bounds Stage 1 already fixed.

This design is notable for credit risk because it sidesteps the question entirely of whether the TFM itself "knows" about monotonicity — it doesn't need to; the guarantee comes from an external, simple, auditable component that wraps around the TFM, and the TFM is relegated to providing a bounded correction signal rather than the primary decision.

The paper situates itself relative to: Zhao et al. (2020), who found that ordinary neural networks frequently violate monotonicity and produce implausible willingness-to-pay estimates in this same discrete-choice setting; Han et al. (2022), who built architecturally-constrained networks that guarantee monotonicity but require redesigning the network per application (the [[classical-monotonic-nn-methods]] approach, applied here); and van Cranenburgh et al. (2022), a survey identifying economic/logical consistency as an open challenge for ML in this domain generally.

## Full-length follow-up (added 2026-11-11)

The same five authors published an extended version: *Embedding Foundation Model Predictions in Discrete-Choice Models with Structural Guarantees* (arXiv:2606.26432). It states that it builds on this workshop paper and adds:
- a **formal preservation result**: a proof that the two-stage adapter keeps the structural model's trade-off ratios (and therefore monotonicity) intact;
- a third dataset (IoT-Wearables) and both Mitra and TabPFN as foundation models;
- a counterfactual aggregate-share test: under a +10% cost increase, the raw foundation models predict *higher* aggregate demand in 6 of 16 scenarios, while the adapter never does;
- a robustness check showing the adapter still gains accuracy when the foundation model gets only a fraction of its usual context.

**For the thesis:** cite the follow-up for the guarantee (the proof is what makes Strategy 1 defensible to a validator) and the workshop paper for the original audit. The aggregate-share test is a good template for a portfolio-level check in credit: does raising every borrower's debt-to-income by 10% ever *lower* the predicted portfolio default rate?

## Relevance to thesis

This is the paper that justifies the entire thesis premise empirically — it shows the *general phenomenon* (TFMs trade away economic/logical consistency for accuracy) is real and measurable, in a domain that is structurally similar to credit risk (both are about predicting probabilities subject to known-direction relationships between inputs and outputs). What it does *not* do: test this in credit risk specifically, where monotonicity isn't just an economic nicety but a literal item in EBA/ECB regulatory guidelines for PD model validation (see [[regulatory-requirements-irb]]). Replicating this audit methodology on a credit/PD dataset, and then testing whether their adapter approach (or an alternative like FairPFN-style prior modification) restores monotonicity without destroying the accuracy advantage TFMs are known for, is close to a fully-specified thesis project.

## See also
[[monotonicity-constraints]], [[regulatory-requirements-irb]], [[credit-risk-pd-modeling]], [[classical-monotonic-nn-methods]]
