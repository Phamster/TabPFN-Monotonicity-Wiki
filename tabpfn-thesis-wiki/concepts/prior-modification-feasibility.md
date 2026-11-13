---
title: Prior Modification for Monotonicity — Feasibility Assessment
tags: [concept, monotonicity, prior-modification, feasibility]
---

# Prior Modification for Monotonicity — Feasibility Assessment

This page examines whether modifying TabPFN's pretraining prior to enforce monotonicity is feasible as a master-thesis contribution, and what it would actually require. See [[monotonicity-enforcement-mechanisms]] for context among the five candidate strategies.

## What "prior modification" means here

TabPFN ([[prior-fitted-networks]]) is trained entirely on synthetic datasets drawn from a generative process — a structural causal model (SCM) prior. The pretrained weights encode that prior's statistical assumptions. FairPFN ([[fairpfn-2024-2025]]) showed you can bias that prior toward a constraint: by generating synthetic SCMs where a protected attribute is an exogenous variable with a specified causal role, the network learns to produce counterfactually fair predictions as a natural output of its in-context mechanism, without any post-hoc correction.

The monotonicity analogue: generate synthetic SCMs where a designated feature has a *monotone causal effect* on the synthetic label — specifically, a feature whose structural equation satisfies ∂Y/∂Xⱼ ≥ 0 (or ≤ 0) everywhere in the synthetic distribution. Training on such SCMs would, in principle, train the network's prior to expect monotone relationships, making violations on real data less likely.

## The core asymmetry between fairness and monotonicity constraints

Counterfactual fairness is a *distributional* constraint. It says: for a given individual, predictions should be the same under different values of the protected attribute. This is a property of the conditional distribution P(Ŷ | X, A) relative to a causal intervention on A — a natural object to represent in an SCM. The SCM formalism is exactly the right language for it, which is why FairPFN's approach transfers cleanly.

Monotonicity is a *pointwise* constraint on the learned function. It says: for every individual, holding all other features constant, Ŷ must not decrease as Xⱼ increases. This is a constraint on the function's partial derivative everywhere — not a property of any distribution, and not a natural object to enforce through SCM structure alone.

This is not a superficial difference. Consider what happens when you generate monotone synthetic SCMs: the structural equation for Y will have monotone dependence on the designated feature within that SCM's distribution. But the transformer is trained on many such SCMs, all with different feature distributions, different nonlinearities, and different interaction structures. What generalizes from that training is a *statistical tendency* to predict monotonically when the context data looks like the synthetic monotone data — not a *mathematical guarantee* of monotone predictions on arbitrary new data. The network's forward pass is a smooth function of the context; there is no logical barrier preventing a non-monotone prediction even if the training distribution was dominated by monotone SCMs.

**Key claim**: prior modification for monotonicity would likely reduce violation rates but cannot guarantee zero violations, unlike the two-stage adapter which achieves the guarantee architecturally.

## What the implementation would actually require

Replicating FairPFN's approach for monotonicity requires:

1. **Access to TabPFN's pretraining code** — not the inference weights (which are public), but the synthetic data generation pipeline and the training loop. Prior Labs has not released this for TabPFN 3.5. The FairPFN authors worked with the TabPFN 2 codebase, which is partially documented in Hollmann et al. (2023) and in the TabPFN GitHub repo; adapting to 3.5 would require reverse-engineering the new prior or waiting for a public release.

2. **GPU compute for pretraining** — FairPFN's 2024 workshop version trained a modified model from scratch; the ICML 2025 version trains from the TabPFN checkpoint using a constraint-aware fine-tuning step. Even fine-tuning requires substantial GPU time (the FairPFN authors report several hours on A100-class hardware). This is not feasible on a laptop. The user has access to a university HPC cluster (pending contact with Prof. Lessmann), which could unblock this if compute is available.

3. **Synthetic SCM design for monotone relationships** — specifically, structural equations of the form Y = f(X₁, ..., g(Xⱼ), ...) where g is monotone increasing/decreasing. This is straightforward to construct; the challenge is ensuring the synthetic distribution remains diverse enough that the pretrained model retains general tabular learning ability rather than overfitting to monotone data.

4. **Evaluation** — the pretrained model's violation rate on held-out real datasets (Koklev + South German) using the same [[price-of-monotonicity-credit-pd-2026]] metric already implemented in this codebase.

## Verdict: feasibility rating

| Criterion | Assessment |
|---|---|
| Implementation complexity | High — requires pretraining code access or clean TabPFN 2 adaptation |
| Compute feasibility (laptop) | Not feasible — pretraining/fine-tuning requires A100-class GPU |
| Compute feasibility (HPC) | Feasible if Lessmann's cluster is accessible |
| Theoretical soundness | Plausible but no guarantee — reduces violations, doesn't eliminate them |
| Novelty as a thesis contribution | High — nobody has published the monotonicity analogue of FairPFN |
| Timeline fit (master's thesis) | Risky — 2–3 months to get pretraining code running and produce meaningful results |

**Recommendation for the thesis**: treat prior modification as a **future work / stretch goal**, not a primary strategy. The contribution can be described as: "We show the prior-modification approach (following FairPFN's methodology) is an open research direction but requires compute and pretraining access beyond the scope of this thesis; strategies 1 and 3 [adapter and context engineering] are tested instead." This framing is honest, positions the gap correctly, and leaves room for a follow-up paper.

If compute access becomes available before the thesis deadline, a lightweight version using fine-tuning from the TabPFN 2 checkpoint (which is public) would be the fastest path to a result.

## What can be done within thesis scope

Even without running the modified prior, the thesis can:
- **Describe** the prior-modification mechanism precisely (this page plus [[fairpfn-2024-2025]])
- **Explain** why the asymmetry between fairness and monotonicity means no guarantee follows from the technique
- **Measure** violation rates of unmodified TabPFN 3.5 (already running via `experiments/run_violations.py`) to quantify the baseline problem the modified prior would need to solve
- **Cite** this as a direction that prior work (FairPFN) proves is *mechanistically possible*, making the case that a future researcher should test it

This gives the thesis a complete conceptual treatment of all five strategies without requiring the most expensive one to be run.

## See also
[[monotonicity-enforcement-mechanisms]], [[fairpfn-2024-2025]], [[prior-fitted-networks]], [[price-of-monotonicity-credit-pd-2026]], [[gap-analysis]]
