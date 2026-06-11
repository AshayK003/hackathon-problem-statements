---
track: rapid-prototype
status: published
---

# JalSathi — Community Water Testing Network

> **Category:** Public Health | Water Quality (India)
> **Build time:** 4–6 weeks (solo developer)

## The Problem

Over 100 million Indians drink groundwater that is contaminated with arsenic, fluoride, nitrate, or uranium at levels exceeding safe limits — a public health crisis on a scale that rivals any epidemic. Chronic exposure causes irreversible health damage: arsenicosis (skin lesions, cancers, cardiovascular disease), fluorosis (crippling skeletal deformity in children), and kidney stones linked to uranium contamination. The damage is cumulative and often goes unnoticed for years until symptoms become debilitating.

The Central Ground Water Board (CGWB) maintains a national network of roughly 15,000 monitoring stations that test groundwater quality across India's 600,000+ villages. But the data from these tests is published in annual PDF reports and academic datasets — formats that are inaccessible to the very communities that need it most. A farmer in rural Rajasthan whose well has fluoride at 5x the safe limit will not know until a child in the family develops skeletal fluorosis years later. Even then, the connection to water quality is rarely made.

Field test kits exist (ranging from ₹200–500 per test), and government programs like the Jal Jeevan Mission (JJM) are investing billions in water quality monitoring. But there is no community-facing tool that connects existing testing data to the people who live on top of contaminated aquifers, enables citizens to self-report test results, and provides actionable guidance on what to do when your water is unsafe. The data exists; the last-mile delivery does not.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| CGWB annual water quality reports | Published as PDFs and spreadsheets; no community-facing interface; 12–18 month data lag |
| Jal Jeevan Mission dashboard | National-level aggregate statistics; does not show village-level water quality data |
| Field test kits (Jal-TARA, H2S vials) | Available but no data aggregation; results are not stored or shared beyond the individual household |
| India Water Portal | Knowledge repository, not a real-time tool; no mapping or alerting capabilities |
| State PHED helplines | Reactive; require citizen to already suspect contamination; no proactive outreach |
| Nothing (majority) | Over 90% of affected villages have no way to access or share water quality information |

## What to Build

- **Water quality map** — Every tested water source pinned on an interactive map with contaminant levels, safe/unsafe indicators, and date of last test
- **Village SMS alert** — Automated SMS when testing data shows contamination in your area: "Alert: Your block's groundwater has arsenic at 5x safe limit. See alternate sources: [link]"
- **Testing kit locator** — Find the nearest place to get a water test kit (PHC, anganwadi, district lab) with contact info and operating hours
- **Community campaign organizer** — Tool to organize a village water testing drive: set a date, invite participants, track results
- **Self-report flow** — WhatsApp-based form to submit your own test results (photo of test strip, GPS location, basic info) which gets pinned on the community map after moderation
- **Alternate water source finder** — Nearest safe drinking water source (piped supply, reverse osmosis plant, protected pond) based on current location
- **SMS subscription** — Weekly water quality digest for your block: "Your block: 3 wells tested. 2 safe, 1 high fluoride. [Action guide link]"
- **Knowledge base** — Water quality information in 8 Indian languages: what each contaminant does, how to treat water, government schemes for safe water access

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Backend | Python FastAPI | Excellent for data ingestion (CGWB CSV/PDF parsing) and SMS workflow orchestration |
| Database | PostgreSQL + PostGIS | Spatial queries for "nearest safe source" and "contamination within 5 km radius" |
| Maps | Leaflet (OpenStreetMap) | Free; no API key required; sufficient for pinning 15,000+ monitoring locations |
| Messaging | Twilio WhatsApp Business + SMS | WhatsApp for rich interaction (photo submission); SMS for alert delivery to feature phones |
| Frontend | Next.js + Tailwind CSS | SSR for SEO on water quality queries; responsive design for low-end phones |
| Data pipeline | GitHub Actions + Pandas | Scheduled scraping and ETL of CGWB reports into structured database |
| Deployment | Railway / Vercel + Supabase | Low-cost hosting; Supabase provides PostgreSQL + real-time subscriptions out of the box |

## Stakeholders

- **100 million+** Indians exposed to unsafe groundwater (conservative estimate; actual likely higher)
- **600,000+** villages that lack any water quality information channel
- **15,000+** CGWB monitoring stations (and growing under JJM)
- **Panchayats (village councils)** — responsible for local drinking water management under the 73rd Amendment
- **ASHA workers and anganwadi workers** — frontline health workers who witness fluorosis and arsenicosis cases
- **PHED (Public Health Engineering Department)** — state-level bodies responsible for water quality testing
- **NGOs** — WaterAid India, UNICEF, Jal Seva, village-level community health organizations

## Why This Is Hackathon-Sized

- **Data already exists** — the challenge is not collection but last-mile delivery and visualization
- **SMS + map + basic forms = core** — no real-time collaboration, no video processing, no complex algorithms
- **Deterministic alert logic** — if contaminant > threshold AND within radius → send SMS; pure if-then rules
- **No ML needed** — no prediction, no anomaly detection, no image recognition in MVP
- **Crowdsourced model is well-understood** — self-report with moderation is a pattern used by hundreds of apps worldwide

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | CGWB data import → interactive water quality map | Parse and geocode CGWB testing data; interactive map with contaminant overlays |
| Week 2 | SMS alert system | Automated SMS to subscribed users when contamination detected in their block |
| Week 3 | Self-report WhatsApp form → pin on map | WhatsApp bot accepting test results (photo + GPS) with moderation dashboard |
| Week 4 | Knowledge base + action guides in 3 languages (Hindi, Marathi, Bengali) | Translated guides on contamination, treatment, and government schemes |
| Week 5 | Alternate water source finder | Nearest safe source locator using PostGIS spatial queries |
| Week 6 | Testing kit locator + village campaign organizer | Map of testing locations; campaign scheduling and tracking |

## Monetization

| Model | Details |
|---|---|
| B2G (PHED department dashboards) | ₹10–₹30 lakh per state per year for water quality analytics and compliance dashboards |
| NGO licensing | ₹5–₹15 lakh per year for white-label platform used in community health programs |
| CSR (corporate water stewardship) | ₹10–₹50 lakh per year from companies needing groundwater data for ESG reporting |
| Open-core (free for communities) | All community-facing features (map, alerts, self-report, knowledge base) are always free |

**Target:** Free for communities; monetize through government and institutional data/analytics services.

## Long-Term Vision

"Weather.com for water quality" — every Indian village knows its water quality score the way it knows today's weather. JalSathi becomes the default source for groundwater quality information in India, used by the Jal Jeevan Mission to prioritize safe water infrastructure investments, by PHED departments to monitor testing coverage, and by millions of families to make informed decisions about their drinking water. Crowdsourced testing data fills the gaps between government monitoring cycles, creating a living map of India's groundwater health.

## Risks

| Risk | Mitigation |
|---|---|
| Self-reported data quality is variable | Implement lab verification badges; require photo of test strip; show "citizen reported" vs. "government tested" labels |
| CGWB data lag (12–18 months from collection to publication) | Mark every data point with "last tested YYYY-MM"; show data freshness indicator |
| Community engagement may decline after initial interest | Village champion program (train local volunteers); gamification (village water quality score) |
| Panic without solutions — alerts without action guidance cause fear | Always pair every contamination alert with a specific, actionable guidance link (boil, filter, alternate source, contact PHED) |
| Coverage gaps — many villages have never been tested | Provide testing kit locator; incentivize community testing drives with public recognition; integrate with JJM testing targets |
