# The Model List

A ranked frontier list for AI models, built the way community "hardest list" sites are built: numbered positions, a main list, an extended list, a legacy list, list points that decay with position, a records table per model, and a lab leaderboard.

Everything is one file, `index.html`, with no build step and no dependencies beyond two Google Fonts families.

## Structure

- **Main list (#1–#15)** — current frontier, full points.
- **Extended list (#16–#30)** — one generation back or smaller tiers, reduced points.
- **Legacy list (#31+)** — history, zero points, never removed.

Points: `250 · 0.888^(p−1)` for the main list, `50 · (31−p)/16` for extended, zero for legacy. A lab's score is the sum of its models' points.

## Editing the list

All data lives in the `MODELS` array near the top of the `<script>` block. Order in the array is rank. Each entry has:

```
id, name, lab, date (YYYY-MM-DD), weights ("open"|"closed"), price, ctx, mark,
blurb, records: [[benchmark, score, "indep"|"vendor"|"community", source, bar 0-100 or null]],
history: [[date, note]]
```

Labs are in `LABS`. The change log on the Guidelines tab is `CHANGELOG`.

## Records and submissions

A record is one benchmark score on one model, tagged by harness (independent, vendor-reported, community) with a source link. The Submit tab writes proposals to a shared queue when the page runs inside the claude.ai artifact viewer. Served anywhere else (GitHub Pages, a local file) the queue is unavailable and the form says so; the list, leaderboard and guidelines work unchanged.

## Running it

Open `index.html` in a browser, or enable GitHub Pages on this repo and point it at the root.
