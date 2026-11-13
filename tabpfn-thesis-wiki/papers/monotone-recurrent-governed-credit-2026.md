---
title: "Learned Monotone Recurrent Features in Governed Credit Scoring: The Price of the Frame and the Necessity of Macro Conditioning"
authors: Tan, Yew Lee (personal capacity)
year: 2026
venue: arXiv
arxiv_id: 2610.08869
tags: [monotonicity, credit-risk, regulatory]
---

# A related "price" concept: what a governance frame costs

Found in the 2026-11-11 gap-watch search. Secondary citation; no TFMs.

## What it does

Asks whether learned, monotone-constrained recurrent features over exposure histories (utilisation, balances, delinquency depth) add value in regulated credit scoring. Each score component comes with a short monotonicity proof, so the model stays auditable.

- **"Price of the frame":** the accuracy a governance frame gives up by restricting which inputs a model may use. The stricter the frame (e.g. only auditable summary features allowed), the more the learned monotone features help; with a large unconstrained feature panel they add nothing.
- Second finding: under a mortgage regime shift, feeding macro series in as plain input columns hurts, while using them to condition the recurrence helps.
- Data: American Express default prediction (primary), Home Credit, Fannie Mae, Freddie Mac, Home Credit Stability, and UCI Taiwan (exploratory).

## Relevance to thesis

- Shows the "price of constraint" framing is spreading beyond Koklev's PoM. Cite it in the Related Work chapter next to [[price-of-monotonicity-credit-pd-2026]].
- Its "strictness ladder" idea could frame your discussion: PoM depends on how strict the governance setting is (which features are constrained, and how).
- Not a competitor: different model class, no foundation models.

## See also
[[price-of-monotonicity-credit-pd-2026]], [[regulatory-requirements-irb]], [[monotonicity-constraints]]
