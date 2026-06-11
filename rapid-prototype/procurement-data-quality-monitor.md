---
track: rapid-prototype
status: published
---

# Open Procurement Data Quality Monitor

> **Category:** Governance | Transparency
> **Build time:** 3–4 weeks (solo developer)

## The Problem

Over 50 countries now publish government procurement data using the Open Contracting Data Standard (OCDS). In theory, this means citizens, auditors, and journalists can see who won which contract, for what amount, and whether the process was competitive.

In practice, the published data is riddled with gaps. Missing buyer names. Redacted award amounts. Inconsistent dates. Entire stages of the contracting process omitted. A 2023 study found that fewer than 20% of OCDS publications meet basic completeness thresholds.

Governments are publishing to check a transparency box, not to enable oversight. Nobody is systematically measuring data quality, tracking it over time, or flagging when it gets worse. Without a quality monitor, bad data is as useless as no data — and provides a false sense of progress.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| Manual audits by transparency orgs | Expensive; done once per country per year at best |
| OCDS validator tool (open source) | CLI-only; no historical tracking; no cross-country comparison |
| National government self-assessments | Conflict of interest; no incentive to report honestly |
| Academic research | Retrospective; 2–3 year publication lag; no real-time alerts |
| Nothing | 80%+ of OCDS publications unevaluated |

## What to Build

A **public data quality monitor** that ingests OCDS data from 10+ countries, runs automated quality checks, and produces per-country health scores with trends and alerts.

**Data ingestion:**
- Pull OCDS JSON packages from government portals (nightly cron)
- Parse and normalize into a uniform schema
- Handle partial, malformed, and versioned records

**Quality checks (automated):**
- **Completeness** — what % of required fields are populated? Are the core fields (buyer, supplier, amount, award date) present?
- **Timeliness** — how long after contract award does the data appear? Is publication within the legally mandated window?
- **Consistency** — do totals add up? Are dates coherent (award before tender)? Do IDs reference existing entities?
- **Granularity** — are individual line items published, or just aggregates? Are bidder names disclosed?
- **Accessibility** — is the data machine-readable? Is there an API or just a static ZIP?

**Outputs:**
- Per-country health score (0–100) computed from quality dimensions
- Trend graphs showing score change over time
- Alert system: email/webhook when a country's score drops by more than 5 points in a month
- Public leaderboard ranking countries by data quality
- Exportable reports for advocacy and audit purposes

No AI. Pure schema validation, data integrity checks, and statistical aggregation.

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Ingestion | Python + requests + pyocds | OCDS ecosystem is Python-native |
| Validation | Custom Python validators + JSON Schema | OCDS has a published JSON Schema; extend with domain rules |
| Database | PostgreSQL + TimescaleDB extension | Time-series friendly for score trends |
| Backend API | Python FastAPI | Lightweight; async data fetching |
| Frontend | Next.js + Chart.js | Public dashboards with interactive charts |
| Charts | Chart.js + react-chartjs-2 | Lightweight; no Mapbox license needed |
| Scheduling | GitHub Actions cron | Free daily ingestion runs |
| Deployment | Railway or fly.io + Neon (Postgres) | Simple single-container deploy |

## Stakeholders

- **Open Contracting Partnership (OCP)** — steward of the OCDS standard; needs quality data to advocate for adoption
- **Transparency International** — 100+ national chapters that audit procurement
- **194 supreme audit institutions** — government auditing bodies that need reliable data
- **Open data activists and civic tech orgs** (Code for Africa, Open Data Charter, etc.)
- **World Bank, IMF, EBRD** — governance indicators and anti-corruption programs
- **Journalists investigating procurement corruption**

## Why This Is Hackathon-Sized

- **Purely computational** — every quality check is a deterministic rule on structured JSON data
- **Data is public** — no auth, no API keys needed; OCDS data is supposed to be open by standard
- **Batch is fine** — daily ingestion via cron is adequate; no real-time requirement
- **Known schema** — OCDS is a published international standard with field-level documentation
- **Impact scales with country count** — once the ingestion pattern is built for 1 country, adding 10 more is a week of connector work

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | OCDS ingestion + storage | Fetch from 3 countries' OCDS endpoints, parse into normalized tables |
| Week 2 | Quality check engine | 10+ automated checks across completeness, timeliness, consistency, granularity |
| Week 3 | Dashboard + charts | Per-country score cards, trend lines, leaderboard |
| Week 4 | Alerts + expansion | Email alerts on score drops; add 5+ more country connectors |

## Monetization

| Model | Details |
|---|---|
| B2G (Open Government Partnership) | $20,000–$50,000/year per country for hosted monitor + support |
| NGO/international org subscription | Transparency International, OCP, World Bank — $30K–$100K/year for global dashboard |
| API access | $1,000/month for raw quality data + webhook alerts |
| Professional services | $10K–$20K per country for OCDS data cleanup + improvement roadmap |

**Target:** Launch with 10 countries using OCP seed funding; sign 3–5 countries as paid subscribers in year one.

## Long-Term Vision

Become the industry-standard watchdog for all open government data quality — not just procurement but budgets (IATI), aid flows (AidData), and beneficial ownership registers. Automated alerts that trigger media investigations when data quality drops. Integration with the Open Data Maturity Index published by the European Data Portal.

## Risks

| Risk | Mitigation |
|---|---|
| Countries change data formats / break endpoints | Build robust error handling; maintain connector tests; get early warning from OCP working group |
| Governments refuse to be ranked | Rankings are based on publicly published data — the data itself is their action, not our opinion |
| Low data quality across the board | Honest baseline is the point. Publish "all countries bad" — pressure for improvement |
| OCDS version changes | Schema version tracking; alert maintainers of breaking changes |
| Funding sustainability | Anchor with OCP/World Bank contract; add paid API tier for commercial users |
