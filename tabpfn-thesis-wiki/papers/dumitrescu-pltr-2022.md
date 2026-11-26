---
title: Machine learning for credit scoring — improving logistic regression with non-linear decision-tree effects (PLTR)
authors: Dumitrescu, Hué, Hurlin, Tokpavi
year: 2022
venue: European Journal of Operational Research 297(3):1178–1192
doi: 10.1016/j.ejor.2021.06.053
tags: [credit, hybrid, interpretability]
---

# Dumitrescu et al. (2022): PLTR

Checked 2026-11-26 via the Crossref deposit; abstract read in the SSRN working-paper version (ScienceDirect
blocked). Thesis bib key `dumitrescu2022machine`.

**Penalised logistic tree regression:** fit short-depth trees on pairs of predictors, turn their rules into
binary predictors, and add them to a penalised (lasso-type) logistic regression. The model captures
non-linear effects and interactions while staying a logistic regression. In simulations and on four credit
datasets PLTR beats plain LR and competes with random forests, while remaining interpretable.

## Relevance to thesis
- **Closest classical relative of the two-stage adapter** ([[monotonicity-enforcement-mechanisms]],
  Strategy 1): both keep an LR as the interpretable core and add an ML component on the logit scale.
  Differences: PLTR adds many tree rules inside one penalised LR; the adapter adds one TabPFN score on the
  free features, and sign bounds on the LR coefficients make the whole model monotone. PLTR has no
  monotonicity guarantee (its tree rules can use any feature).
- Use in Ch. 2 (PD modelling) and Ch. 3 (adapter) for positioning; EJOR, so in the Lessmann/Baesens orbit.

## See also
[[credit-risk-pd-modeling]], [[economic-validity-audit-2026]], [[rudin-interpretable-2019]]
