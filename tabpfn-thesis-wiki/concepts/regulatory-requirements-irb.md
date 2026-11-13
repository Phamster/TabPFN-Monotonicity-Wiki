---
title: Regulatory Requirements for IRB / PD Models
tags: [concept, regulatory]
---

# Regulatory Requirements — the non-ML side of the gap

Captures the regulatory framing established earlier in the thesis-planning process, kept separate from the ML literature above so it's easy to update as CRR3/ECB guidance evolves without touching the ML pages.

## Key constraints relevant to TFM feasibility

- **Interpretability ("white box") expectations** — Article 189 CRR language, EBA guidance — models must be explainable enough for supervisors and internal validation functions to challenge them. TFMs, as transformers operating via in-context learning, are arguably *harder* to satisfy here than gradient-boosted trees, where SHAP/TreeSHAP is well-established tooling. See [[shap-and-monotonicity]] for the complication that monotonicity constraints introduce to SHAP explanations.
- **Monotonicity / economically sensible risk drivers** — implicit in EBA Guidelines on PD/LGD estimation and in supervisory expectations that risk drivers behave sensibly. This is the regulatory anchor for the [[monotonicity-constraints]] stream of this wiki. [[mathematical-certification-monotonicity-2024]] cites both EBA and CRR explicitly in its motivation, confirming this is the right anchor.
- **Generalization / overfitting concerns** — the ECB's 2025 internal models guide explicitly flags that ML approaches have more degrees of freedom and are therefore more prone to underestimating out-of-sample error, especially relevant to TFMs' in-context mechanism, which has not been studied under distribution shift the way gradient-trained models have.
- **Calibration requirements** — EBA GL on PD estimation require calibrated (not just discriminating) PD estimates. See [[calibration-vs-discrimination]] for why this is distinct from AUC performance and why the Brier-PoM is a necessary complement to the AUC-PoM in your results.
- **Approval process** — ECB and EBA discussion papers (2022-2023) confirm ML algorithms for IRB are not yet in mainstream supervisory-approved use; a handful of institutions have submitted ML-based IRB model components for review, with outcomes still pending as of the most recent EBA follow-up report.
- **CRR3 (effective Jan 2025) / 2025 ECB internal models guide** — added an explicit machine learning section to the ECB's guide, signaling regulators are actively developing more specific expectations rather than treating ML as out of scope.

## Monotonicity sub-criteria (from Chen & Ye 2023)

[[chen-ye-monotonicity-mrm-2023]] provides a useful formal decomposition of what "satisfying monotonicity" means in a model risk management context:
- **Global monotonicity**: the function is monotonic over the entire input space (what XGBoost's native `monotone_constraints` achieves)
- **Local monotonicity**: monotonic in the neighborhood of the training data (weaker — what empirical testing typically checks)
- **Marginal monotonicity**: increasing a feature marginally always moves prediction in the right direction

The two-stage adapter (Strategy 1) achieves global monotonicity in Stage 1's constrained logistic regression. Whether it maintains this globally when Stage 2's correction is added is not formally certified — see [[mathematical-certification-monotonicity-2024]] for the certification framework that would be needed to prove this.

## How this connects to the TFM literature
None of the TFM papers in this wiki engage with this regulatory language directly — they're written for an ML audience, testing accuracy/fairness/monotonicity as abstract properties, not as the specific named criteria a supervisor would check against (Art. 189 explainability, EBA GL on PD/LGD monotonicity, ECB generalization expectations). Translating between the two literatures — mapping "does TabPFN satisfy monotonicity in a discrete-choice sense" to "does TabPFN satisfy the specific monotonicity expectations implicit in EBA GL on PD and LGD estimation" — is itself a contribution a thesis could make, independent of any new empirical result.

## See also
[[monotonicity-constraints]], [[credit-risk-pd-modeling]], [[gap-analysis]]
