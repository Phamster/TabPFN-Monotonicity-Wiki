---
title: TabPFN-3
authors: Prior Labs (Hollmann et al.)
year: 2026
venue: Prior Labs release (May 2026)
arxiv_id: n/a (model release; check HuggingFace/Prior Labs docs for technical report)
tags: [tfm, foundational]
---

# TabPFN-3 — the current release as of mid-2026

Released May 2026. Supports datasets with up to **one million rows and 200 features** — a dramatic leap from TabPFN v2's 10K-sample ceiling and TabPFN-2.5's ~100K ceiling. This makes the scalability objection that previously pushed large credit datasets (Lending Club, GMSC) outside TabPFN's scope substantially less relevant.

## What this means for the thesis benchmark

If you're running experiments now (mid-2026), you should benchmark against TabPFN-3, not TabPFN v2 or even TabPFN-2.5 — using an older checkpoint would mean your results are not representative of the current TFM state of the art, and a reviewer could reasonably object. Check the Prior Labs HuggingFace page for the latest checkpoint name and any API changes.

The scale increase also changes the experiment design slightly: you can now run TabPFN-3 on Lending Club or GMSC directly (both ~150K rows) rather than having to subsample, which removes a confound that was present in the earlier experiment design. This is worth noting explicitly in the methodology chapter.

## Does the monotonicity question change?

Probably not in direction, possibly in degree. A larger, more capable model might have *more* violations of monotonicity (more complex decision boundaries) or *fewer* (better generalization). The honest answer is: we don't know, and that's one of the reasons testing it is valuable. The economic-validity-audit paper ([[economic-validity-audit-2026]]) was run on TabPFN v2 and Mitra — TabPFN-3 is untested on any monotonicity criterion.

## Practical note on authentication

TabPFN-3 likely requires the same HuggingFace token + Prior Labs terms acceptance as earlier versions. Confirm at `huggingface.co/Prior-Labs` before starting experiments. The license (Prior Labs License v1.1) explicitly permits research use and benchmarking but restricts commercial/production use — fine for a thesis.

## See also
[[tabpfn-2.5-2025]], [[tabpfn-v2-2025]], [[tabular-foundation-models-landscape]]
