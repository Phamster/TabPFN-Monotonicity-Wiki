---
title: Causal Pre-training Under the Fairness Lens — An Empirical Study of TabPFN
authors: Liu, Qinyi; Khalil, Mohammad; Goel, Naman
year: 2026
venue: Proceedings of the ACM Web Conference 2026 (WWW '26)
arxiv_id: 2601.17912
tags: [tfm, fairness]
---

# Does TabPFN's causal pretraining help fairness "for free"?

A very recent (Jan 2026) empirical study asking whether TabPFN's synthetic-SCM pretraining — designed for general predictive accuracy, not fairness — happens to confer any fairness benefits as a side effect, purely because the model is reasoning over plausible causal mechanisms rather than memorizing spurious dataset-specific correlations. This connects to a claim made elsewhere (see the credit-risk-TFM speculative paper) that PFN-style pretraining might "temper historical biases" simply by virtue of its synthetic, causally-structured training distribution.

**Finding (added 2026-11-11):** TabPFN is more accurate than the baselines and robust to spurious correlations, but its fairness gains are moderate and inconsistent, especially under missing-not-at-random covariate shift. The authors conclude causal pretraining helps but is not enough on its own. Benchmarks: Heart, Bank, Law, Adult (no credit data). Note: the "speculative credit-risk paper" this page used to link to turned out to be an empirical benchmark — see [[foundation-models-credit-risk-2026]].

## Relevance to thesis

This is the paper to read closely if you want to know whether vanilla TabPFN (no FairPFN-style modification) already has some baseline fairness property worth measuring before you build anything more elaborate. It's also a useful empirical counterpart to the credit-risk paper's speculation — that paper *hypothesizes* causal pretraining helps fairness; this one actually tests it (on general benchmarks, not credit data specifically). A thesis chapter could explicitly extend this empirical methodology to a credit-risk dataset, which would be a clean, well-scoped contribution.

## See also
[[counterfactual-fairness]], [[prior-fitted-networks]]
