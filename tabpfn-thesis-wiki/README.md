# Wiki Schema & Conventions

This is a personal research wiki on **tabular foundation models (TFMs), monotonicity enforcement, and fairness** — built for a Master's thesis exploring whether TFMs (TabPFN and relatives) can satisfy regulatory constraints (monotonicity, fairness, explainability) when applied to credit risk / PD modeling.

Pattern follows the "LLM Wiki" idea (raw sources → compiled wiki → schema). See: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

## Layers

- **`sources/catalog.md`** — the source-of-truth bibliography. Every paper referenced anywhere in the wiki must have an entry here (title, authors, year, venue, arXiv ID, URL). This wiki does NOT store full PDFs (network/copyright constraints) — only paraphrased notes with links back to originals. Treat this file as close to immutable; only append.
- **`papers/`** — one page per paper. Summarizes contribution, method, findings, and *relevance to the thesis* in the author's own words (never verbatim quotes beyond a few words). Links out to `concepts/` pages.
- **`concepts/`** — synthesis pages that cut across multiple papers (e.g., "Monotonicity Constraints", "Prior-Fitted Networks"). These are where the actual thinking lives — they should evolve as new papers are ingested.
- **`overview.md`** — top-level synthesis tying the three streams (TFM landscape, fairness, monotonicity) together.
- **`gap-analysis.md`** — the living document tracking the actual thesis research gap as it sharpens over time. This is the most important file — update it whenever a new paper confirms, narrows, or closes the gap.
- **`index.md`** — content-oriented catalog of every page with one-line summaries. Read this first when answering a query.
- **`log.md`** — chronological, append-only record of ingests and major edits. Entries start with `## [YYYY-MM-DD] ingest | Title` so they're greppable.

## Conventions

- Use `[[wikilink]]`-style links (Obsidian syntax) between pages — e.g., `[[prior-fitted-networks]]`.
- Every paper page has YAML frontmatter: `title`, `authors`, `year`, `venue`, `arxiv_id`, `tags`.
- Tags vocabulary (keep controlled): `tfm`, `fairness`, `monotonicity`, `credit-risk`, `regulatory`, `foundational`, `survey`.
- When a new paper contradicts or updates an existing claim, don't silently overwrite — note the supersession explicitly in the relevant concept page (e.g., "as of the TabPFN-2.5 release, this benchmark result no longer holds").

## Operations

**Ingest** a new paper: add to `sources/catalog.md` → write/update its `papers/` page → update every `concepts/` page it touches → update `index.md` → append to `log.md` → revisit `gap-analysis.md` to see if the gap has shifted.

**Query**: read `index.md` first, then `gap-analysis.md` for thesis framing, then drill into the specific `papers/` or `concepts/` pages needed.

**Lint**: periodically check for orphan pages (no inbound links), concepts mentioned in paper pages but lacking their own concept page, and claims in `gap-analysis.md` that newer ingests may have invalidated.

## Status

Seeded in one session (2026-06-17) from ~20 papers found via web search. This is a **starting corpus**, not exhaustive — treat it as scaffolding to keep extending as you read more deeply (especially via backward/forward citation snowballing from the seed papers).
