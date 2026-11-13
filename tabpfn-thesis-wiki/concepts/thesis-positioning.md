---
title: Thesis Positioning — Differentiation from Existing Work
tags: [concept, synthesis]
---

# Thesis Positioning

The most practically important concept page in the wiki. Synthesises what the deep-dive literature search confirmed: the gap is real but narrower than it looked in the first pass, and you need explicit differentiation statements for at least five papers. Write this page before writing the thesis introduction.

> **Update 2026-11-11:** the gap-watch search found the gap still open, but changed two things. (1) [[foundation-models-credit-risk-2026]] is an empirical 14-dataset benchmark co-authored by Lessmann, not a speculative paper; its differentiation entry and the "so what" framing below are rewritten. (2) A new per-constraint PoM paper ([[shapley-pom-decomposition-2026]]) needs its own entry.

## The positioning statement (draft, revised 2026-11-11)

*"Recent benchmarks show that tabular foundation models such as TabPFN-3 are now the most accurate models for credit PD prediction (Baesens et al. 2026). Before banks can use them for internal ratings, they must also satisfy the monotonicity expectations of credit risk regulation. We ask: what is the Price of Monotonicity for tabular foundation models on credit PD data, and does it exceed the GBM-established baseline — particularly on small datasets where TFMs claim their accuracy advantage? Existing work has benchmarked monotonicity costs for gradient-boosted trees (Koklev 2025; Alonso-Robisco et al. 2025, 2026) and has documented monotonicity violations in TFMs in transport economics (Wang et al. 2026), but the credit risk domain — where monotonicity is a regulatory requirement rather than a preference — has not been addressed for TFMs. We fill this gap by (1) benchmarking the Price of Monotonicity for TabPFN using the same metric and datasets as the GBM baseline, enabling direct comparison; and (2) testing two enforcement mechanisms that exploit TFMs' inference-time architecture — a post-hoc adapter and context engineering — neither of which exists in traditional gradient-boosted models."*

## Paper-by-paper differentiation

### vs. Koklev (2025)
**Overlap**: Same metric (PoM), same general question (what does monotonicity cost in credit PD), overlapping datasets.
**Distinction**: Koklev studies GBMs only. We study TFMs. GBM monotonicity enforcement (native `monotone_constraints`) has no analogue in TFMs — the enforcement mechanisms are entirely different, and so is the question of whether they can work.

### vs. Alonso-Robisco et al. (2025)
**Overlap**: XGBoost + monotonicity + credit risk. Both use Lending Club. Both engage with regulatory framing.
**Distinction**: Their question is *who* is affected by constraints (distributional impact, fairness implications, Shapley regression). Our question is *how much accuracy* is lost by different enforcement mechanisms, and *whether* those mechanisms can be applied to TFMs at all. Completely different research questions using the same general setup.

### vs. Chen & Ye (2022)
**Overlap**: Monotonic neural network architecture for credit scoring.
**Distinction**: MNAM is trained from scratch per dataset. Our thesis studies pre-trained TFMs where no gradient training on the user's data occurs at inference time. The enforcement challenge is structurally different — you can constrain a training objective, but you cannot add a loss term to a single forward pass.

### vs. Economic validity audit (2026)
**Overlap**: Tests TFM monotonicity violations and proposes an adapter. Direct methodological template.
**Distinction**: Transport economics, not credit risk. Stakes and regulatory framing are categorically different. Their adapter targets discrete-choice utility monotonicity (economics theory); ours targets credit risk regulatory monotonicity (EBA/ECB guidance). Attribution: the PoM metric is Koklev's and the adapter is theirs; our contribution is the transfer to TFMs in credit risk and the direct comparison with the GBM baseline. Cite the full-length follow-up (arXiv:2606.26432) for the formal guarantee.

### vs. Baesens, Lessmann et al. (2026) — TFMs for credit risk benchmark *(rewritten 2026-11-11)*
**Overlap**: TFMs for credit PD; TabPFN-3; several of the same public datasets (German, GMSC, LendingClub, Taiwan); regulatory framing in the introduction.
**Distinction**: They measure accuracy and calibration of nine TFMs out of the box, and find TabPFN-3 best. They do not test monotonicity or any regulatory constraint, and they do not enforce anything. We take their accuracy result as the starting point and ask whether it survives monotonicity enforcement, and at what price.
**How to handle it**: build on it rather than contrast with it. Your supervisor is a co-author, so frame the thesis as the constraint-compliance follow-up to that benchmark. Their calibration finding (TabPFN-3 underpredicts default rates) also motivates reporting Brier-PoM next to AUC-PoM.
*(The old entry said "that paper speculates; this thesis tests". That was wrong and must not appear in the thesis.)*

### vs. Alonso-Robisco et al. (2026) — Shapley decomposition of PoM *(new 2026-11-11)*
**Overlap**: PoM in credit scoring; German, Taiwan and Polish data.
**Distinction**: XGBoost only; asks which individual constraints cause the cost. We ask what the cost is for TFMs under different enforcement mechanisms. Optional bridge: apply their per-constraint decomposition to TabPFN with the adapter. Only a Zenodo replication package is public so far; locate the manuscript before citing. See [[shapley-pom-decomposition-2026]].

### vs. FairPFN (2025)
**Overlap**: Modifying TFM behavior to satisfy a constraint (there: fairness; here: monotonicity). FairPFN is the methodological template for Strategy 2.
**Distinction**: Different constraint type (causal fairness vs. feature-output monotonicity). We do not implement prior modification — we test whether two cheaper alternatives (adapter, context engineering) can achieve the same outcome without retraining.

## The "so what" framing for different audiences

**For Lessmann's chair (IS/OR focus)**: the chair's own benchmark (Baesens, Lessmann et al. 2026) shows TabPFN-3 is the most accurate PD model. Before banks can use it for internal ratings, they need to know whether regulatory monotonicity requirements can be satisfied, and at what accuracy cost. We provide the first empirical answer.

**For an ML conference (if the thesis becomes a paper)**: We extend the TFM benchmark literature from accuracy-only evaluation to include regulatory-constraint evaluation, introducing PoM as a criterion alongside AUC. We test two novel enforcement mechanisms with no GBM equivalent.

**For a regulator or practitioner**: We tell you concretely whether TabPFN's accuracy advantage over XGBoost survives the constraint enforcement required by EBA/ECB guidance — and which enforcement strategy minimizes the accuracy cost.

## See also
[[gap-analysis]], [[overview]], [[regulatory-requirements-irb]], [[foundation-models-credit-risk-2026]], [[shapley-pom-decomposition-2026]]
