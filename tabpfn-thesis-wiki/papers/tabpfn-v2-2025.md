---
title: TabPFN v2 (Accurate predictions on small data with a tabular foundation model)
authors: Hollmann, Müller, Purucker, Krishnakumar, Körfer, Hoo, Schirrmeister, Hutter
year: 2025
venue: Nature
arxiv_id: n/a (Nature publication)
tags: [tfm, foundational]
---

# TabPFN v2 (2025, Nature)

The version that turned TFMs from a curiosity into a serious contender against gradient-boosted trees. Scales the original 2023 architecture to handle larger datasets (up to ~10,000 samples) and adds support for both classification and regression, missing values, categorical features, and outliers without manual preprocessing.

Beyond raw prediction, the paper demonstrates that the pretrained network has genuine **foundation model properties**: it can estimate feature densities (useful for anomaly/fraud detection), generate synthetic data approximating the joint distribution, and produce reusable embeddings. Notably, the authors use the **German Credit Dataset** as one of their proof-of-concept showcases for density estimation — meaning credit risk data was already used to demonstrate TabPFN's capabilities, just not in a way that engages with the *regulatory* requirements credit risk modeling actually has to satisfy.

## Relevance to thesis

This is the benchmark every later comparison (including a thesis benchmark) would be measured against. The credit-data showcase is a hook: it shows TabPFN's authors implicitly gesture toward credit risk as a natural application domain, but the demonstration is purely about density estimation capability, not about default prediction, calibration, monotonicity, or any regulatory criterion. That gap — TabPFN touches credit data, but never the specific things a regulator cares about — is part of the open space this thesis could occupy.

## See also
[[prior-fitted-networks]], [[tabular-foundation-models-landscape]], [[credit-risk-pd-modeling]]
