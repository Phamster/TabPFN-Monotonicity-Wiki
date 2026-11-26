# Source Catalog

The bibliography of record. Every paper below is referenced in at least one `papers/` page. No full texts are stored here (network/copyright constraints) — only metadata and links. Use these links to download the actual PDFs yourself for citation and close reading.

## Tabular Foundation Models — Core Architecture

| Paper | Authors | Year | Venue | Link |
|---|---|---|---|---|
| Transformers Can Do Bayesian Inference (PFN paper) *(added 2026-11-26)* | Müller, Hollmann, Pineda Arango, Grabocka, Hutter | 2022 | ICLR | arXiv:2112.10510 |
| Statistical Foundations of Prior-Data Fitted Networks *(added 2026-11-26)* | Nagler | 2023 | ICML (PMLR 202) | arXiv:2305.11097 |
| TabPFN: A Transformer That Solves Small Tabular Classification Problems in a Second | Hollmann, Müller, Eggensperger, Hutter | 2023 | ICLR | arXiv:2207.01848 |
| Accurate predictions on small data with a tabular foundation model (TabPFN v2) | Hollmann, Müller, Purucker, Krishnakumar, Körfer, Hoo, Schirrmeister, Hutter | 2025 | Nature | nature.com/articles/s41586-024-08328-6 |
| TabPFN-2.5: Advancing the State of the Art in Tabular Foundation Models | Grinsztajn, Flöge, Key, Birkel, et al. (Prior Labs) | 2025 | arXiv | arXiv:2511.08667 |
| **TabPFN-3 (May 2026 — up to 1M rows)** | Prior Labs | 2026 | Model release | huggingface.co/Prior-Labs |
| TabICL: A Tabular Foundation Model for In-Context Learning on Large Data | Qu, Holzmüller, Varoquaux, Le Morvan | 2025 | ICML | arXiv:2502.05564 |
| TabICLv2: A better, faster, scalable, and open tabular foundation model | Qu, Holzmüller, Varoquaux, Le Morvan | 2026 | arXiv | arXiv:2602.11139 |
| Mitra: Mixed Synthetic Priors for Enhancing Tabular Foundation Models | Zhang et al. (AutoGluon team) | 2025 | NeurIPS | huggingface.co/autogluon/mitra |
| Table Foundation Models: on knowledge pre-training for tabular learning | (survey) | 2025 | arXiv | arXiv:2505.14415 |
| Position: tabular foundation models should be a research priority | van Breugel, van der Schaar | 2024 | ICML (position paper) | — |
| **Tabular Foundation Models Are Near-Redundant: Diversity, Ensembling, and the State of the Art** | (per arXiv) | 2026 | arXiv | arXiv:2605.18696 |
| **Exploring Fine-Tuning for Tabular Foundation Models** | (per arXiv) | 2026 | arXiv | arXiv:2601.09654 |
| Pocket Foundation Models: Distilling TFMs into CPU-Ready Gradient-Boosted Trees *(added 2026-11-11)* | Tanna, Bouarour, Bouadi, Sankarapu, Seth | 2026 | arXiv | arXiv:2605.18654 |
| Do Tabular Foundation Models Agree with Themselves? *(added 2026-11-11)* | (per arXiv) | 2026 | arXiv | arXiv:2608.06004 |

## Fairness × Tabular Foundation Models

| Paper | Authors | Year | Venue | Link |
|---|---|---|---|---|
| FairPFN: Transformers Can do Counterfactual Fairness | Robertson, Hollmann, Awad, Hutter | 2024 | arXiv / AIES workshop / Master's thesis | arXiv:2407.05732 |
| FairPFN: A Tabular Foundation Model for Causal Fairness | Robertson et al. | 2025 | ICML | arXiv:2506.07049 |
| Towards Fair In-Context Learning with Tabular Foundation Models | Kenfack et al. | 2025 | arXiv | arXiv:2505.09503 |
| Causal Pre-training Under the Fairness Lens: An Empirical Study of TabPFN | Liu, Khalil, Goel | 2026 | WWW '26 (ACM Web Conference) | arXiv:2601.17912 |

## Monotonicity Enforcement — Classical, Recent, and Credit-Specific

| Paper | Authors | Year | Venue | Link |
|---|---|---|---|---|
| Deep Lattice Networks and Partial Monotonic Functions | You, Ding, Canini, Pfeifer, Gupta | 2017 | NeurIPS | arXiv:1709.06680 |
| Certified Monotonic Neural Networks | Liu, Han, Zhang, Liu | 2020 | NeurIPS | proceedings.neurips.cc |
| Counterexample-Guided Learning of Monotonic Neural Networks (COMET) | Sivaraman et al. | 2020 | NeurIPS | arXiv:2006.08852 |
| Constrained Monotonic Neural Networks | Runje, Shankaranarayana | 2023 | ICML | proceedings.mlr.press/v202/runje23a |
| Expressive Monotonic Neural Networks | (authors per arXiv) | 2023 | ICLR | arXiv:2307.07512 |
| Scalable Monotonic Neural Networks | (authors per ICLR) | 2024 | ICLR | proceedings.iclr.cc |
| Monotonic decision trees (Potharst & Feelders 2002; Velikova & Daniels 2004; Hu et al. 2012; Marsala & Petturiti 2015; Pei et al. 2016) | various | 2002-2016 | various | see [[classical-monotonic-decision-trees]] |
| MonoNet: enhancing interpretability in neural networks via monotonic features | (authors per Bioinformatics Advances) | 2023 | Bioinformatics Advances | academic.oup.com/bioinformaticsadvances |
| A new flexible and partially monotonic discrete choice model | Kim, Bansal | 2024 | Transportation Research Part B | sciencedirect.com S0191261524000717 |
| Auditing and Fixing Economic Validity in Tabular Foundation Models for Discrete Choice | Wang, Sun, Li, Fan, Zhuang | 2026 | ICML 2026 Workshop (FMSD) | arXiv:2605.26559 |
| Embedding Foundation Model Predictions in Discrete-Choice Models with Structural Guarantees *(added 2026-11-11; full-length follow-up of the above)* | Wang, Sun, Li, Fan, Zhuang | 2026 | arXiv | arXiv:2606.26432 |
| Talking Trees: Reasoning-Assisted Induction of Decision Trees for Tabular Data | (authors per arXiv) | 2026 | arXiv | arXiv:2509.21465 |
| **What's the Price of Monotonicity? A Multi-Dataset Benchmark of Monotone-Constrained Gradient Boosting for Credit PD** | Koklev, Petr | 2025/2026 | arXiv / SSRN | arXiv:2512.17945 |
| **Constrained Machine Learning Models for Credit Default Prediction: Who Wins, and Who Loses?** | Alonso-Robisco, Carbo, de Haro, Guillén García | 2025 | EUI RSC Working Paper 2025/24 | cadmus.eui.eu |
| Decomposing the Price of Monotonicity Constraints with Shapley Values in Credit Scoring *(added 2026-11-11; manuscript not yet located)* | Alonso-Robisco, Carbó, De Haro Rodríguez, Garcia Guillen | 2026 | replication package (Zenodo) | doi:10.5281/zenodo.23982617 |
| Learned Monotone Recurrent Features in Governed Credit Scoring: The Price of the Frame and the Necessity of Macro Conditioning *(added 2026-11-11)* | Tan, Yew Lee | 2026 | arXiv | arXiv:2610.08869 |
| **Monotonic Neural Additive Models: Pursuing Regulated Machine Learning Models for Credit Scoring** | Chen, Dangxing; Ye, Weicheng | 2022 | ACM ICAIF 2022 | arXiv:2209.10070 |
| **How to Address Monotonicity for Model Risk Management?** | Chen, Dangxing; Ye, Weicheng | 2023 | ICML 2023 | proceedings.mlr.press/v202 pp.5282-5295 |
| **A Mathematical Certification for Positivity Conditions in Neural Networks** | (per arXiv) | 2024 | arXiv | arXiv:2406.08525 |
| **Can I Trust the Explanations? Investigating XAI Methods for Monotonic Models** | (per arXiv) | 2023 | arXiv | arXiv:2309.13246 |
| **Interpretable Credit Scoring via Monotonic Neural Networks** | (per CSBulletin) | 2025 | Computer Science Bulletin | csbulletin.com |
| **Instance-Wise Monotonic Calibration by Constrained Transformation (MCCT)** | (per arXiv) | 2025 | arXiv | arXiv:2507.06516 |
| **Domain-Constrained Stacking Framework for Credit Default Prediction** | (per MDPI) | 2025 | MDPI Mathematics 13(21):3451 | mdpi.com |
| Online and Linear-Time Attention by Enforcing Monotonic Alignments *(terminology trap — see [[mononet-and-terminology-trap]])* | Raffel et al. | 2017 | ICML | arXiv:1704.00784 |

## Fairness in ML — Classical Foundations

| Paper | Authors | Year | Venue | Link |
|---|---|---|---|---|
| Equality of Opportunity in Supervised Learning | Hardt, Price, Srebro | 2016 | NeurIPS | arXiv:1610.02413 |
| Data preprocessing techniques for classification without discrimination | Kamiran, Calders | 2012 | Knowledge and Information Systems | — |
| Certifying and Removing Disparate Impact | Feldman, Friedler, Moeller, Scheidegger, Venkatasubramanian | 2015 | KDD | — |

## Tabular Foundation Models × Credit Risk

| Paper | Authors | Year | Venue | Link |
|---|---|---|---|---|
| Tabular Foundation Models for Credit Risk Prediction: A Dedicated Review and Empirical Comparison (v1/v2 title: Foundation Models for Credit Risk Prediction: A Game Changer?) | Baesens, Goethals, Lessmann, De Vos, Bravo, Martens, Medina-Olivares, Mues, Oskarsdóttir, vanden Broucke, Van Gestel, Verdonck, Verbeke | 2026 (v3 Oct 2026) | arXiv (invited review) | arXiv:2605.18147 |
| Data Presentation Over Architecture: Resampling Strategies for Credit Risk Prediction with Tabular Foundation Models | Tanna et al. | 2026 | arXiv | arXiv:2605.18635 |
| TabICL Under the Microscope: Benchmarking Tabular Foundation Models for Enterprise Credit Risk | Subramaniyan (Mission Lane) | 2026 | industry blog, non-peer-reviewed | medium.com/mission-lane-tech-blog |

## Adjacent / Background (from earlier literature pass)

| Paper | Authors | Year | Venue | Link |
|---|---|---|---|---|
| Benchmarking state-of-the-art classification algorithms for credit scoring | Lessmann, Baesens, Seow, Thomas | 2015 | European Journal of Operational Research | — |
| Fairness in credit scoring: Assessment, implementation and profit implications | Kozodoi, Jacob, Lessmann | 2022 | European Journal of Operational Research | — |
| Machine learning for credit scoring: Improving logistic regression with non-linear decision-tree effects (PLTR) *(added 2026-11-26)* | Dumitrescu, Hué, Hurlin, Tokpavi | 2022 | European Journal of Operational Research 297(3) | doi:10.1016/j.ejor.2021.06.053 |
| Stop explaining black box machine learning models for high stakes decisions and use interpretable models instead *(added 2026-11-26)* | Rudin | 2019 | Nature Machine Intelligence 1(5) | doi:10.1038/s42256-019-0048-x |
| Explainable AI for Operational Research | De Bock, Coussement, De Caigny, Lessmann et al. | 2024 | European Journal of Operational Research | — |

*Note: author lists marked "per arXiv" are abbreviated from search snippets — verify full author lists against the primary source when citing.*
