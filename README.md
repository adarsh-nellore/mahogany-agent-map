# Mahogany — Agent Architecture (Live Graph)

An animated, single-file visualization of how **Mahogany's** regulatory-intelligence agents pull
regulatory events/news and match them to the products a user tracks.

It's a force-directed "living graph" (D3 v7) that reads left → right:

**Sources → fetch tiers → ingestion agents → Signals Pool → synthesis → your digest**

- **Sources** (left): **132 feeds** across FDA/openFDA, EMA (CHMP·PRAC·MDCG), MHRA, Health Canada, TGA, PMDA, WHO/IMDRF/ICH, ClinicalTrials.gov, and industry press. Click **"View all 132 sources"** for the full catalog, grouped by region with tier badges.
- **Fetch tiers**: RSS · API · Firecrawl — fast poll every 4h; deep scrape daily.
- **Ingestion agents**: Fetcher Orchestrator → Quality Gate & Dedup → Classifier (Claude Haiku 4.5) → Embedder (text-embedding-3-small).
- **Your product** (top): Entity Resolver → Watch Items → Relevance Scorer + Profile Search Agent reach into the shared Signals Pool to pull matches.
- **Delivery** (right): Feed Agent (Claude Sonnet 4) → Feed Stories → Digest Agent → email via Resend → you.

Animated particles show data flowing along the "tentacles"; a narration bar (bottom-right) steps
through the pipeline; hover any node for its role.

## Run it

It's one self-contained file — just open `index.html` in a browser. D3 loads from CDN, so an
internet connection is needed for the graph to render.

## Deploy

Static site, zero config. On Vercel: import this repo and deploy (framework preset: *Other*).

---

*Demo-friendly labels reflect the real pipeline (agent names, models, cadences).*
