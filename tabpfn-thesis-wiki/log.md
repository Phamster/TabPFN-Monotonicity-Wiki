# Log

Append-only. Format: `## [YYYY-MM-DD] ingest | Title` for greppability (`grep "^## \[" log.md`).

## [2026-06-17] ingest | TabPFN (original, 2023)
First wave seeding session. Web search + abstract review (no PDF download — network/copyright constraints). See [[papers/tabpfn-2023]].

## [2026-06-17] ingest | TabPFN v2 (Nature, 2025)
See [[papers/tabpfn-v2-2025]]. Noted German Credit Dataset showcase as a thesis hook.

## [2026-06-17] ingest | TabPFN-2.5 (2025/2026)
See [[papers/tabpfn-2.5-2025]]. Current SOTA vs. XGBoost as of this session.

## [2026-06-17] ingest | TabICL / TabICLv2 (2025/2026)
See [[papers/tabicl-2025-2026]]. Includes non-peer-reviewed industry benchmark (Mission Lane) — flagged as such.

## [2026-06-17] ingest | Mitra + van Breugel position paper (2025/2024)
See [[papers/mitra-and-position-paper]].

## [2026-06-17] ingest | FairPFN (2024 workshop/thesis + 2025 ICML)
See [[papers/fairpfn-2024-2025]]. Identified as the template for prior-modification constraint enforcement.

## [2026-06-17] ingest | Kenfack et al., Fair In-Context Learning (2025)
See [[papers/kenfack-fair-icl-2025]]. Context-selection mechanism, complementary to FairPFN.

## [2026-06-17] ingest | Causal Pre-training Under the Fairness Lens (2026)
See [[papers/causal-pretraining-fairness-2026]]. Empirical test of whether vanilla pretraining helps fairness.

## [2026-06-17] ingest | Classical monotonic NN methods (2017-2024, six papers)
See [[papers/classical-monotonic-nn-methods]]. Established the pre-TFM toolkit baseline.

## [2026-06-17] ingest | Economic Validity Audit of TFMs for Discrete Choice (2026)
See [[papers/economic-validity-audit-2026]]. **Flagged as the single most important paper for the gap analysis.**

## [2026-06-17] ingest | Talking Trees (2026)
See [[papers/talking-trees-2026]]. Secondary/supporting citation only.

## [2026-06-17] ingest | Foundation Models for Credit Risk Prediction: A Game Changer? (2026)
See [[papers/foundation-models-credit-risk-2026]]. Flagged as closest existing competitor — speculative, not empirical.

## [2026-06-17] ingest | Resampling Strategies for Credit Risk Prediction with TFMs (2026)
See [[papers/resampling-credit-risk-tfm-2026]]. Solid empirical baseline for context-construction effects.

## [2026-06-17] ingest | Classical fairness-in-ML foundations (2012-2015)
See [[papers/classical-fairness-ml]]. Hardt/Price/Srebro, Kamiran/Calders, Feldman et al.

## [2026-06-17] synthesis | Overview + Gap Analysis written
First full pass synthesizing all ingests above into [[overview]] and [[gap-analysis]]. Recommended framing: replicate-and-extend the monotonicity audit into credit risk.

---
*Next session: consider backward/forward citation snowballing from [[economic-validity-audit-2026]] and [[fairpfn-2024-2025]] specifically — these are the highest-leverage seed papers for finding closely related work this search pass may have missed.*

## [2026-06-17] ingest | Deep-dive pass: monotonicity enforcement mechanisms
Requested follow-up: go deeper specifically on how monotonicity could be enforced on TFMs, and fold in what the chat conversation had already surfaced (the economic-validity-audit two-stage adapter, classical monotonic NN methods). Ran four additional targeted searches.

## [2026-06-17] ingest | Economic Validity Audit (2026) — enriched
Updated [[papers/economic-validity-audit-2026]] with the full two-stage adapter mechanism (Stage 1 sign-constrained MNL, Stage 2 frozen-parameter correction term), exact accuracy-recovery numbers, and related citations (Zhao et al. 2020, Han et al. 2022, van Cranenburgh et al. 2022).

## [2026-06-17] ingest | Price of Monotonicity — Koklev (2025/2026) — MAJOR
See [[papers/price-of-monotonicity-credit-pd-2026]]. **Flagged as the most consequential single ingest of this session** — a rigorously quantified GBM-side Price-of-Monotonicity baseline for credit PD across 5 public datasets and 3 libraries, materially sharpening [[gap-analysis]] from "explore whether TFMs violate monotonicity in credit risk" to "measure the Price of Monotonicity for TFMs, directly comparable to this published GBM baseline."

## [2026-06-17] ingest | Classical monotonic decision trees + Kim & Bansal partially-monotonic DCM
See [[papers/classical-monotonic-decision-trees]]. Adds the "partial, not global monotonicity" framing relevant to which credit-risk features actually need constraining.

## [2026-06-17] ingest | MonoNet + monotonic-attention terminology trap
See [[papers/mononet-and-terminology-trap]]. Fourth candidate TFM-monotonicity mechanism (output-head-only constraint) plus a flagged search-time trap (monotonic attention ≠ feature monotonicity).

## [2026-06-17] synthesis | New deep-dive concept page + gap-analysis rewrite
Created [[concepts/monotonicity-enforcement-mechanisms]] consolidating all four candidate strategies with a comparison table. Substantially rewrote [[gap-analysis]] to reflect the sharpened framing (Price-of-Monotonicity-for-TFMs vs. the Koklev GBM baseline as the lead recommendation). Trimmed and updated [[concepts/monotonicity-constraints]] to link out rather than duplicate.

## [2026-06-17] ingest | Deep literature search pass — "are there papers already doing this?"
Ran targeted searches on: (1) monotonicity+TFM+benchmark, (2) constrained ML+credit default+who wins, (3) post-hoc monotonicity correction+credit, (4) TabPFN+fine-tuning+monotonicity+regulatory. Key question: does anything in the literature already do what the thesis proposes? Answer: no, but the gap is narrower than the first pass suggested.

## [2026-06-17] ingest | Alonso-Robisco et al. (2025) — Who Wins and Who Loses
Already added earlier. **Flagged as critical differentiation paper.** See [[papers/alonso-robisco-who-wins-loses-2025]]. Closest published work to the XGBoost portion of the thesis. Differentiation: they ask "who is affected," thesis asks "what does it cost a TFM and which enforcement mechanism minimizes that cost."

## [2026-06-17] ingest | Chen & Ye (2022) ICAIF — Monotonic NAMs for credit scoring
Already added. Closest architectural competitor to Strategy 4. See [[papers/chen-ye-monotonic-nam-2022]].

## [2026-06-17] ingest | Chen & Ye (2023) ICML — How to address monotonicity for model risk management
NEW. Critical for regulatory chapter vocabulary — provides global/local/marginal monotonicity sub-criteria. See [[papers/chen-ye-monotonicity-mrm-2023]].

## [2026-06-17] ingest | Mathematical certification for positivity/partial monotonicity (2024) arXiv:2406.08525
NEW. Explicitly cites EBA follow-up report and CRR. Provides certification framework that is the logical complement to enforcement. See [[papers/mathematical-certification-monotonicity-2024]].

## [2026-06-17] ingest | Can I Trust the Explanations? (2023) arXiv:2309.13246
Already added. SHAP behavior on constrained models. See [[papers/trust-explanations-monotonic-2023]].

## [2026-06-17] ingest | MonoNet applied to credit scoring with counterfactuals (2025) CSBulletin
NEW. Strategy 4's architectural idea applied directly to credit scoring. Counterfactual angle opens secondary analysis opportunity. See [[papers/monoet-credit-scoring-2025]].

## [2026-06-17] ingest | Instance-wise Monotonic Calibration (MCCT) (2025) arXiv:2507.06516
NEW. Third post-hoc adapter option (simpler than two-stage, addresses different monotonicity aspect). See [[papers/instance-wise-monotonic-calibration-2025]].

## [2026-06-17] ingest | Domain-Constrained Stacking (2025) MDPI Mathematics
Already added. WoE-based monotonicity; conceptual predecessor to Strategy 1. See [[papers/domain-constrained-stacking-2025]].

## [2026-06-17] ingest | TFMs Near-Redundant (2026) arXiv:2605.18696
Already added. Key finding: don't need to test all 6 TFMs; TabPFN v2.5 leads on 153 datasets. See [[papers/tfm-near-redundant-2026]].

## [2026-06-17] ingest | TabPFN-3 (May 2026 release)
Already added. Supports 1M rows — scale ceiling gone. Use this for experiments, not earlier checkpoints. See [[papers/tabpfn-3-2026]].

## [2026-06-17] ingest | Fine-tuning for TFMs (2026) arXiv:2601.09654
Already added. Mechanical support for Strategy 4. Also cites TabTune library. See [[papers/fine-tuning-tfm-2026]].

## [2026-06-17] synthesis | New concept pages added
Added [[concepts/calibration-vs-discrimination]], [[concepts/woe-encoding-and-monotonicity]]. Updated [[concepts/tabular-foundation-models-landscape]] with near-redundancy finding and TabPFN-3 scale shift. Updated [[concepts/regulatory-requirements-irb]] with Chen & Ye 2023 sub-criteria and mathematical certification EBA connection.

## [2026-06-17] synthesis | Threat map completed
See [[concepts/thesis-positioning]] for paper-by-paper differentiation table. Conclusion: gap is real but narrower — five papers need explicit differentiation, not just citation. Alonso-Robisco et al. and Chen & Ye 2022 are the two most important to read in full before writing the literature review.

## [2026-11-11] ingest | Gap-watch search (first since 2026-06-17)
Searched TabPFN/TFM + monotonicity + credit, TFMs for credit PD, Price of Monotonicity, monotone in-context learning, fairness × TFM × credit, EBA ML/IRB, Koklev follow-ups. Result: **no paper tests TFMs against monotonicity on credit data; the gap is still open.** Details in [[gap-analysis]] ("What changed (2026-11-11)").

## [2026-11-11] correction | Baesens, Lessmann et al. — TFMs for credit risk (arXiv:2605.18147 v3) — MAJOR
Rewrote [[papers/foundation-models-credit-risk-2026]]. The June page called it speculative; it is a 9-TFM × 14-dataset PD benchmark (plus LGD), co-authored by Stefan Lessmann. TabPFN-3 best on average; TFMs underpredict default rates; no monotonicity tested. Updated [[concepts/thesis-positioning]], [[overview]], [[gap-analysis]], [[index]] and the catalog to match.

## [2026-11-11] ingest | Adapter follow-up (arXiv:2606.26432)
Added to [[papers/economic-validity-audit-2026]]: full-length version with a formal preservation proof, a third dataset and a counterfactual aggregate-share test. Workshop paper venue now known (ICML 2026 FMSD); authors filled in.

## [2026-11-11] ingest | Decomposing the PoM with Shapley values (Alonso-Robisco et al., Zenodo)
NEW. See [[papers/shapley-pom-decomposition-2026]]. Only the replication package is public; locate the manuscript before citing.

## [2026-11-11] ingest | Pocket Foundation Models (arXiv:2605.18654)
NEW. See [[papers/pocket-foundation-models-distillation-2026]]. Basis for a fifth enforcement idea (distil into a monotone-constrained XGBoost), added to [[concepts/monotonicity-enforcement-mechanisms]].

## [2026-11-11] ingest | Monotone recurrent features / price of the frame (arXiv:2610.08869)
NEW, secondary. See [[papers/monotone-recurrent-governed-credit-2026]].

## [2026-11-11] ingest | Do TFMs agree with themselves? (arXiv:2608.06004)
NEW, secondary. See [[papers/tfm-self-consistency-2026]].

## [2026-11-11] update | Causal pre-training fairness study
Filled in authors and venue (WWW '26) and the main finding in [[papers/causal-pretraining-fairness-2026]].

## [2026-11-24] update | Candidate Strategy 6: post-hoc rearrangement
Added to [[monotonicity-enforcement-mechanisms]]: sort/isotonic-repair each borrower's TabPFN PD curve along the constrained features. Idea only, for the supervisor; citations still to verify.

*Next gap-watch: early December 2026. Re-check arXiv:2605.18147 section 6.2 (future work) in the PDF, and look for the Shapley-PoM manuscript.*
