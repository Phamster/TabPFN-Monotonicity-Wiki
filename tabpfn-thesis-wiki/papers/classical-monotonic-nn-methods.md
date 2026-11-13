---
title: Classical & recent monotonic neural network methods
authors: You/Ding/Canini/Pfeifer/Gupta (2017); Liu/Han/Zhang/Liu (2020); Sivaraman et al. (2020); Runje/Shankaranarayana (2023); various (2023-2024)
year: 2017-2024
venue: NeurIPS / ICML / ICLR
arxiv_id: 1709.06680 / various
tags: [monotonicity, foundational]
---

# The monotonic-ML toolbox (pre-TFM)

A cluster of six related papers spanning the standard approaches to enforcing monotonicity in neural networks, none of which target TFMs specifically — they're the established toolkit a thesis would adapt or compare against.

**Deep Lattice Networks (You et al., 2017)** — combines linear embeddings, lattice ensembles, and piecewise-linear calibrators, with linear-inequality constraints on the lattice parameters guaranteeing monotonicity by construction. Reliable but parameter-hungry and structurally rigid (the lattice structure itself restricts the hypothesis space).

**Certified Monotonic Neural Networks (Liu et al., 2020)** — takes a different tack: train an ordinary network with a monotonicity regularization term in the loss, then *verify* monotonicity post-hoc using mixed-integer linear programming (treating ReLU networks' piecewise-linear structure as a verification problem). Outperforms Deep Lattice Networks and Min-Max nets in their benchmarks.

**COMET (Sivaraman et al., 2020)** — counterexample-guided learning: iteratively find inputs where monotonicity is violated, add them to the training set, repeat. A different verification philosophy from the MILP-certification approach.

**Constrained / Expressive / Scalable Monotonic Networks (2023-2024)** — a recent wave addressing the core complaint about all earlier methods: that guaranteed-monotonic architectures sacrifice too much expressiveness. These propose monotonicity-preserving activation function designs that retain more of a standard network's flexibility.

## Relevance to thesis

None of this literature touches transformers or in-context learning — it's all parametric, gradient-trained networks. That's exactly the gap: the *mechanisms* for enforcing monotonicity (constrained architecture, post-hoc verification, counterexample-guided retraining, prior-injection à la FairPFN) are well-developed in isolation, but nobody has asked which of these mechanisms — if any — is even applicable to an in-context-learning model that never receives gradient updates on your data at inference time. A TFM's "training" is just the original synthetic pretraining; you can't add a monotonicity regularizer to a forward pass. This is a genuine methodological puzzle worth a thesis chapter on its own: do these classical techniques even transfer to the TFM paradigm, or does monotonicity in TFMs require an entirely different enforcement strategy (e.g., the FairPFN-style prior modification, or post-hoc output correction)?

## See also
[[monotonicity-constraints]], [[prior-fitted-networks]], [[in-context-learning-tabular]]
