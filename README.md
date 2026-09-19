# The Model List

A ranked frontier list for AI models, built the way community "hardest list" sites are built: numbered positions, a main list, an extended list, a legacy list, a watchlist, list points that decay with position, benchmark scores per model, a benchmark cross-reference grid, and a lab leaderboard.

Live at https://rulednotebook.github.io/model-list/

Everything is one file, `index.html`, with no build step and no dependencies beyond two Google Fonts families.

## Structure

- **Main list (#1–#15)** — current frontier, full points.
- **Extended list (#16–#30)** — one generation back or smaller tiers, reduced points.
- **Legacy list (#31+)** — history, zero points, never removed.
- **Watchlist** — announced models with no benchmark result yet. Unranked.

Placement is by measured capability only. Restricted and internal models are ranked on their published numbers and carry a status badge; availability never moves a model.

Points: `250 · 0.888^(p−1)` for the main list, `50 · (31−p)/16` for extended, zero for legacy. A lab's score is the sum of its models' points.

## Pages

- **List** — the ranked rail with movement since the last issue, and a page per model: headline stats, benchmark scores with where each stands against the rest of the list, specs, placement history.
- **Lab leaderboard** — labs ranked by summed points, with how many benchmarks each lab leads.
- **Benchmarks** — a grid of main-list (or all ranked) models against the key benchmarks, best score per column highlighted, plus a one-line description of each benchmark.
- **Guidelines** — placement rules, points formula, change log.

Deep links work: `#model/gpt-6-astra`, `#labs/openai`, `#benchmarks`, `#guidelines`. Press `/` to search, arrow keys to move through the list.

## Editing the list

All data lives in the `<script>` block near the top of the JavaScript:

- `MODELS` — the ranked list. Order in the array is rank. Each entry:

  ```
  id, name, lab, date (YYYY-MM-DD), status ("ga"|"restricted"|"internal"|"preview"),
  weights ("open"|"closed"), price, ctx, mark, blurb,
  scores: [[benchmark, score, "indep"|"vendor"|"community", source, bar 0-100 or null]],
  history: [[date, note]]
  ```

  Benchmark names must match exactly across models for standings and the grid to line up.

- `PREV_ISSUE` — the order of the previous issue, used to compute movement arrows. Copy the current `MODELS` order here before you reorder.
- `WATCH` — announced but unbenchmarked models.
- `BENCH_COLS` — which benchmarks the grid shows, with short labels and descriptions.
- `LABS`, `CHANGELOG` — as named.

## Not tracked

Records. On a list like this a record would be the best thing built with a single model in a set period, not a benchmark score. That is subjective enough that the list does not track it yet.
