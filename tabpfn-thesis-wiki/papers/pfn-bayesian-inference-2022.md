---
title: Transformers Can Do Bayesian Inference (the PFN paper)
authors: Müller, Hollmann, Pineda Arango, Grabocka, Hutter
year: 2022
venue: ICLR
arxiv_id: 2112.10510
tags: [tfm, foundational, theory]
---

# PFN paper (2022): the method behind every TabPFN

Introduces **Prior-Data Fitted Networks** ([[prior-fitted-networks]]): sample many datasets from a prior over
data-generating mechanisms, hold out points, and train a transformer to predict the held-out labels from the
rest. The trained network then approximates the **posterior predictive distribution** (PPD) for a new dataset
in a single forward pass. Shown on Gaussian processes, Bayesian neural networks, and small tabular and
few-shot tasks. TabPFN ([[tabpfn-2023]]) is this method with a prior built from structural causal models.

Checked 2026-11-26 against arXiv (v1 Dec 2021; ICLR 2022, OpenReview KSugKcbNf9).

## Key result (the one the thesis uses)
- **Corollary 1.1** (Sec. 3, "PPD Approximation with PFNs"; proof in Appendix A, eqs. 5–9): the PFN training
  loss equals E_{D,x}[ KL( p(·|x,D) || q_θ(·|x,D) ) ] plus a constant C = −E_{x,D}[ H(p(·|x,D)) ] that does not
  depend on θ. It follows from "Insight 1": the loss is the expected cross-entropy between the PPD and q_θ.
- A footnote in the 2024 arXiv update says the result appeared first in Foong et al. (2020), Sec. 3.2, Prop. 1.
  Cite both if the thesis states it (check Foong et al. before adding to the bib).

## Relevance to thesis
- Source for the "PFN = approximate Bayesian inference" step in Ch. 2/3 and for the KL/Pinsker argument in
  `rem:ppd-limits` (b) of `chapters/theory/ppd_monotone.tex` (thesis bib key `muller2022transformers`).
- The guarantee is an **expected** KL over prior-drawn contexts and queries, so it says nothing about rare
  queries (off-support ICE grid points): this is why a monotone prior would not guarantee a monotone network
  ([[prior-modification-feasibility]]).

## See also
[[prior-fitted-networks]], [[tabpfn-2023]], [[in-context-learning-tabular]], [[fairpfn-2024-2025]]
