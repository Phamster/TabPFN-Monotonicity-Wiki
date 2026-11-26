# Index

Read this first. Organized by category; each entry links to its page with a one-line summary.

## Start here
- [[overview]] — synthesis across all three streams, the shape of the literature
- [[gap-analysis]] — the living document on what's actually novel for the thesis (read this second)
- [[thesis-positioning]] — explicit differentiation statements vs. every nearby paper; draft positioning sentence

## Concepts (cross-paper synthesis — the real content)
- [[prior-fitted-networks]] — what a PFN is, why the synthetic prior controls everything downstream
- [[in-context-learning-tabular]] — why context-window construction rivals model choice in importance
- [[tabular-foundation-models-landscape]] — map of TFM lineages; near-redundancy finding; TabPFN-3 scale shift
- [[monotonicity-constraints]] — the core gap; why classical tooling doesn't mechanically transfer to TFMs
- [[monotonicity-enforcement-mechanisms]] — **key concept**: five strategies (distillation added 2026-11-11), comparison table, evidence per strategy
- [[prior-modification-feasibility]] — **(new 2026-11-13)** detailed feasibility assessment of Strategy 2 (prior modification for monotonicity); verdict: future work, not thesis scope
- [[calibration-vs-discrimination]] — **(new)** why Brier-PoM matters as much as AUC-PoM for regulatory purposes
- [[woe-encoding-and-monotonicity]] — **(new)** the industry's traditional monotonicity solution and why it doesn't transfer to TFMs
- [[shap-and-monotonicity]] — SHAP value behavior under constraints; TreeSHAP vs. KernelSHAP practical note
- [[counterfactual-fairness]] — group vs. counterfactual fairness, why the distinction matters for thesis scoping
- [[credit-risk-pd-modeling]] — bridges this wiki to the Lessmann/regulatory literature
- [[regulatory-requirements-irb]] — CRR/EBA/ECB language including monotonicity sub-criteria from Chen & Ye 2023

## Papers — Tabular Foundation Models (core architecture)
- [[pfn-bayesian-inference-2022]] — **(new 2026-11-26)** the PFN method paper (ICLR 2022); loss = expected KL to the PPD + const
- [[nagler-pfn-statistical-foundations-2023]] — **(new 2026-11-26)** PFN theory: pre-tuned untrained predictor; bias vanishes only if localised
- [[tabpfn-2023]] — the original proof of concept (ICLR 2023)
- [[tabpfn-v2-2025]] — Nature paper, 10K samples, German Credit Dataset showcase
- [[tabpfn-2.5-2025]] — 100% win rate vs. XGBoost on small/medium data, distillation
- [[tabpfn-3-2026]] — **(new)** May 2026 release, 1M rows — scale ceiling gone, use this for experiments
- [[tabicl-2025-2026]] — scale-focused lineage; Mission Lane credit-risk industry benchmark
- [[mitra-and-position-paper]] — AutoGluon's TFM + position paper
- [[tfm-near-redundant-2026]] — **(new)** six TFMs produce near-redundant predictions; TabPFN v2.5 leads on 153 datasets
- [[fine-tuning-tfm-2026]] — **(new)** fine-tuning TFMs; mechanical support for Strategy 4 output-head constraint
- [[pocket-foundation-models-distillation-2026]] — **(new 2026-11)** distilling TFMs into XGBoost/CatBoost; basis for Strategy 5
- [[tfm-self-consistency-2026]] — **(new 2026-11)** every TFM fails probabilistic self-consistency checks; supports behavioural audits

## Papers — Fairness × TFM
- [[fairpfn-2024-2025]] — prior modification for counterfactual fairness (workshop → ICML 2025)
- [[kenfack-fair-icl-2025]] — context-selection for group fairness, no retraining needed
- [[causal-pretraining-fairness-2026]] — does vanilla pretraining help fairness for free? (WWW '26: helps, but not enough)

## Papers — Monotonicity (classical and credit-specific)
- [[classical-monotonic-nn-methods]] — Deep Lattice, Certified, COMET, Constrained, Expressive, Scalable networks
- [[classical-monotonic-decision-trees]] — monotonic decision trees + Kim & Bansal partial monotonicity
- [[mononet-and-terminology-trap]] — MonoNet output-head idea + terminology trap (monotonic attention ≠ feature monotonicity)
- [[chen-ye-monotonic-nam-2022]] — Monotonic NAMs for credit scoring (ACM ICAIF 2022)
- [[chen-ye-monotonicity-mrm-2023]] — **(new)** How to address monotonicity for model risk management (ICML 2023); global/local/marginal sub-criteria
- [[mathematical-certification-monotonicity-2024]] — **(new)** formal certification of partial monotonicity; cites EBA/CRR directly
- [[trust-explanations-monotonic-2023]] — Can you trust SHAP on monotonically constrained models?
- [[monoet-credit-scoring-2025]] — **(new)** MonoNet applied to credit scoring with counterfactual explanations
- [[instance-wise-monotonic-calibration-2025]] — **(new)** MCCT: post-hoc monotonic calibration as constrained transformation; third adapter option
- [[economic-validity-audit-2026]] — **the key paper**: TFMs violate monotonicity ~50% of the time; full two-stage adapter mechanics; 2026 follow-up adds a formal guarantee
- [[price-of-monotonicity-credit-pd-2026]] — **the GBM baseline**: PoM 0–2.9% AUC across 5 datasets and 3 libraries
- [[alonso-robisco-who-wins-loses-2025]] — XGBoost + monotonicity + Lending Club; Shapley regression analysis of who is affected
- [[shapley-pom-decomposition-2026]] — **(new 2026-11)** same group: Shapley decomposition of PoM per constraint (XGBoost); natural add-on analysis
- [[monotone-recurrent-governed-credit-2026]] — **(new 2026-11)** "price of the frame": cost of governance restrictions in credit scoring (no TFMs)
- [[domain-constrained-stacking-2025]] — WoE-based monotonicity in a stacking ensemble; conceptual predecessor to Strategy 1
- [[talking-trees-2026]] — secondary citation: TFMs lack constraint mechanisms generally

- [[dumitrescu-pltr-2022]] — **(new 2026-11-26)** PLTR: LR + tree-rule effects; closest classical relative of the adapter
- [[rudin-interpretable-2019]] — **(new 2026-11-26)** interpretable by design instead of post-hoc explanation

## Papers — Credit Risk × TFM
- [[foundation-models-credit-risk-2026]] — **closest competitor, co-authored by Lessmann**: 9 TFMs × 14 PD datasets, TabPFN-3 best, underpredicts PD; no monotonicity (corrected 2026-11-11)
- [[resampling-credit-risk-tfm-2026]] — solid empirical benchmark: context strategy > TFM choice on accuracy

## Papers — Classical Foundations (fairness)
- [[classical-fairness-ml]] — Hardt/Price/Srebro, Kamiran/Calders, Feldman et al.; pre/in/post-processing taxonomy

## Sources
- [[../sources/catalog]] *(file: sources/catalog.md)* — full bibliography with arXiv IDs and links
