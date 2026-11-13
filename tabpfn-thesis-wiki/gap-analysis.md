---
title: Gap Analysis — Living Document
tags: [synthesis, gap]
---

# Gap Analysis

**Update this page every time a new paper is ingested.** Last updated: 2026-11-11 (gap-watch search: gap still open, but the credit-risk × TFM picture changed; see "What changed (2026-11-11)" at the end). Previous update: 2026-06-17.

## The gap, stated precisely (updated)

No published work empirically tests whether tabular foundation models (TabPFN family, TabICL, Mitra, etc.) satisfy the **monotonicity** expectations implicit in credit risk regulatory guidance (EBA GL on PD/LGD, ECB internal models guide — see [[regulatory-requirements-irb]]) when applied to actual default/PD data. Two things are now true that weren't true after the first pass:

1. The GBM-side baseline for "what does monotonicity cost in credit PD" is **no longer missing** — [[price-of-monotonicity-credit-pd-2026]] rigorously quantifies it (a Price of Monotonicity of roughly 0-2.9% AUC across three GBM libraries and five public credit datasets, smallest on large portfolios, largest on small/heavily-constrained ones). This means the thesis question is no longer "does monotonicity cost anything in credit PD" (answered) but specifically **"what is the equivalent Price of Monotonicity when the underlying model is a TFM rather than a GBM, using which enforcement mechanism, and does the cost scale with dataset size the same way?"**
2. The *mechanisms* available for enforcing monotonicity on a TFM are now enumerated with concrete technical detail in [[monotonicity-enforcement-mechanisms]] (four candidates: post-hoc adapter, prior modification, context engineering, output-head constraint), with the post-hoc adapter being both the most directly evidenced (via [[economic-validity-audit-2026]]) and the cheapest to implement.

The closest existing analog, [[economic-validity-audit-2026]], demonstrates the *general phenomenon* — TFMs trade economic consistency for accuracy — and a working fix, in transport economics, not credit risk. The stakes are categorically different in credit risk (a discrete-choice model behaving oddly is a curiosity; a PD model behaving non-monotonically is a potential regulatory disqualifier under EBA/ECB expectations), and the specific quantitative baseline to compare against ([[price-of-monotonicity-credit-pd-2026]]) didn't exist for either domain until this most recent search pass.

A secondary, slightly less open gap: no one has tested either of the two existing TFM-fairness mechanisms ([[fairpfn-2024-2025]]'s prior modification, [[kenfack-fair-icl-2025]]'s context selection) on real credit/PD data, despite [[foundation-models-credit-risk-2026]] raising PFN pretraining as a possible help with exactly this.

## Three candidate thesis framings, ranked by how cleanly they're scoped (updated)

**1. Measure the Price of Monotonicity for TFMs in credit risk, directly comparable to the GBM baseline (strongest fit — sharpened by this pass)**
Adopt [[price-of-monotonicity-credit-pd-2026]]'s exact PoM metric and bootstrap methodology. Implement the post-hoc adapter mechanism from [[economic-validity-audit-2026]] (Stage 1: sign-constrained logistic regression/scorecard; Stage 2: frozen Stage-1 parameters + a correction term using a TFM's raw PD prediction as additional input) on one or more of the same five public datasets Koklev uses, or a comparable substitute if those aren't fully reproducible. Report PoM for TFM+adapter alongside Koklev's GBM numbers on the *same or comparable* dataset, broken out by dataset size — directly testing whether the "monotonicity is costlier on small data" pattern Koklev finds for GBMs also holds for TFMs, which is a particularly sharp question given TFMs' selling point is exactly strong small-data performance. As a stretch extension, test context engineering (strategy 3 in [[monotonicity-enforcement-mechanisms]]) as a second, even-cheaper-to-implement mechanism and compare its PoM against the adapter's.

**2. Test whether causal pretraining helps fairness on real credit data**
Extend [[causal-pretraining-fairness-2026]]'s empirical methodology (currently run on general fairness benchmarks) to a credit dataset, directly testing the claim raised in [[foundation-models-credit-risk-2026]] that PFN pretraining might temper historical biases (that paper benchmarks accuracy and calibration but does not test fairness). Well-scoped, but more contested territory since [[fairpfn-2024-2025]] and [[kenfack-fair-icl-2025]] are already a crowded, well-resourced sub-field — harder to differentiate.

**3. Map regulatory language to ML metrics formally**
A more conceptual contribution: build a rigorous mapping between the specific monotonicity/explainability language in EBA/ECB guidance ([[regulatory-requirements-irb]]) and measurable ML properties, then audit several TFMs against that formal rubric. Lower empirical risk, but also lower novelty ceiling — closer to a literature/policy contribution than an ML contribution.

## Recommendation given current corpus (updated)
Framing 1 is now considerably sharper than after the first pass: it has a named metric to adopt (PoM), a named mechanism to implement (the two-stage adapter, already proven in a structurally similar domain), a named baseline to compare against (Koklev's GBM numbers), and — if the same public datasets are reused — a path to results that are *directly numerically comparable* to an existing benchmark rather than requiring a freestanding justification of dataset choice and evaluation protocol from scratch. This is about as well-scoped as an open ML research gap gets.

## What would close this gap (watch for these)
- Any paper directly combining "TabPFN"/"TFM" + "monotonicity" + "credit" or "PD" in its abstract — would directly compete with Framing 1.
- Any extension of [[price-of-monotonicity-credit-pd-2026]] itself to non-GBM model families (the author frames this as a GBM-specific benchmark, but a follow-up extending to TFMs is exactly what this thesis would be).
- A new EBA/ECB publication that explicitly addresses TFMs/transformers (current guidance only mentions "machine learning" generically).
- Prior Labs or a competing TFM vendor publishing a credit-risk-specific case study that engages with regulatory criteria rather than pure accuracy. *(2026-11-11: none found; no sign that TabPFN supports monotone constraints natively.)*
- **A follow-up to [[foundation-models-credit-risk-2026]] by the Baesens/Lessmann group** that adds constraint compliance or monotonicity. This is now the most likely source of direct competition — ask Lessmann about it.
- The manuscript behind [[shapley-pom-decomposition-2026]] extending to non-GBM models.

## What changed in this update (2026-06-17, second pass)
Went deeper specifically on monotonicity-enforcement mechanisms per request. Found: (a) [[price-of-monotonicity-credit-pd-2026]] — a rigorous, already-published GBM-side PoM baseline for credit PD that didn't surface in the first search pass; (b) much richer technical detail on the [[economic-validity-audit-2026]] two-stage adapter mechanism (exact Stage 1/Stage 2 structure, accuracy-recovery numbers); (c) two additional candidate enforcement mechanisms — [[classical-monotonic-decision-trees]]'s partial-monotonicity framing (Kim & Bansal) and [[mononet-and-terminology-trap]]'s output-head-only constraint idea — bringing the total candidate mechanism count from three to four, now organized in a dedicated comparison page, [[monotonicity-enforcement-mechanisms]]; (d) a terminology trap worth remembering (the "monotonic attention" literature is unrelated — sequence-alignment monotonicity, not feature-output monotonicity). Net effect: Framing 1 went from "a clean gap" to "a clean gap with a ready-made metric, mechanism, and baseline to build directly on."

## What changed (2026-11-11, gap-watch search)

Searched for anything since 2026-06-17 combining TFMs, monotonicity, credit risk and PoM. **No paper tests TFMs against monotonicity on credit data, so Framing 1 is still open.** Changes:

1. **Correction — the credit-risk × TFM stream is not thin any more.** [[foundation-models-credit-risk-2026]] (Baesens, Goethals, **Lessmann** et al.; v3 Oct 2026) is a 14-dataset empirical benchmark, not a speculative paper. TabPFN-3 is the best PD and LGD model on average, and TFMs underpredict default rates. It tests no monotonicity. This strengthens Framing 1: the accuracy premise is now settled by the supervisor's own group, and the regulatory-constraint question is the obvious next step. It also makes that group the most likely competitor (watchlist above).
2. **Strategy 1 now has a formal guarantee:** the adapter's full-length follow-up (arXiv:2606.26432, see [[economic-validity-audit-2026]]) proves the adapter preserves the structural model's monotonicity.
3. **New GBM-side PoM work:** [[shapley-pom-decomposition-2026]] decomposes PoM per constraint with Shapley values (XGBoost only). Not a competitor, but a natural add-on analysis.
4. **A fifth enforcement idea:** distil TabPFN-3 into a monotone-constrained XGBoost, building on [[pocket-foundation-models-distillation-2026]]. Added to [[monotonicity-enforcement-mechanisms]].
5. Supporting citations: [[monotone-recurrent-governed-credit-2026]] ("price of the frame") and [[tfm-self-consistency-2026]] (TFMs fail behavioural consistency checks).
6. Nothing new from the EBA/ECB on ML or TFMs in IRB models (2026 changes only concern model-change approvals). No new version of Koklev (still v2, March 2026).

## See also
[[overview]], [[monotonicity-constraints]], [[monotonicity-enforcement-mechanisms]], [[price-of-monotonicity-credit-pd-2026]], [[economic-validity-audit-2026]], [[foundation-models-credit-risk-2026]], [[regulatory-requirements-irb]]
