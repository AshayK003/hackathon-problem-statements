---
track: rapid-prototype
status: published
---

# School Resource Transparency Map

> **Category:** Education | Infrastructure
> **Build time:** 4–6 weeks (solo vibe-coder)

## The Problem

Across Africa, South Asia, and Latin America, government reports claim schools have electricity, toilets, textbooks, and clean water. On the ground, the reality is very different.

A school might be listed as "electrified" but the connection was cut two years ago. "Textbooks provided" might mean one teacher's copy for 60 students. "Toilet facilities" could be a pit latrine that collapsed last rainy season. Nobody is doing ground-truth audits at scale. The national Education Management Information System (EMIS) relies on self-reported data from head teachers who fear budget cuts if they report honestly.

Parents, journalists, and advocacy groups have no way to verify what their children's school actually has. Education ministries make resource allocation decisions based on fiction. Donor programs claim impact that doesn't exist.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| EMIS (national education data systems) | Self-reported by head teachers; political incentives to inflate; 1–3 year data lag |
| School report cards (gov-issued) | Published rarely; aggregated; no GPS; hard to verify |
| NGO spot audits | Expensive; small sample size; not sustained |
| Parent word of mouth | Doesn't scale; no central record |
| Nothing | Most common. Nobody knows what's actually happening in 90% of schools. |

## What to Build

A **mobile-first platform (offline-capable)** for creating school profiles with ground-truth resource audits. Designed for a phone carried by a parent, a local journalist, or an advocacy group volunteer.

**School profile creation:**
- GPS coordinates captured on-site
- School name, type (primary/secondary), enrollment count
- Photo of the school entrance (geotagged)

**Resource audit checklist:**
- Electricity: working connection? Hours per day? Solar backup?
- Water: tap? borehole? well? seasonal? Distance from classrooms?
- Toilets: number of stalls? Boys/girls separate? Working? Lockable?
- Textbooks: counts by subject and grade? Student-to-book ratio?
- Classrooms: total rooms? In good repair? Roof leaks? Chairs/desks?
- Computers / ICT: number of working devices? Internet access?
- School feeding: meals provided? Kitchen? Water source for cooking?

**Scorecard (0–100):**
- Computed automatically from checklist responses
- Broken into sub-scores: Infrastructure, Water/Sanitation, Learning Materials, ICT
- Color-coded (red < 40, amber 40–70, green > 70)

**Dashboard:**
- Color-coded map showing every school audited
- Filter by district, resource type, score range
- Compare government-claimed data vs. ground-truth data side by side
- Trend view: re-audit a school quarterly to track improvement or decline

**Offline-first:**
- Full app works without internet
- SQLite local storage; syncs when connected
- SMS fallback for minimal data submission (if app can't sync)

No AI. Checklists, math, maps, and comparisons.

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Mobile framework | React Native (Expo) | Cross-platform; offline-first with SQLite |
| Local database | SQLite (via expo-sqlite) | Full offline audit capability |
| Cloud backend | Supabase (Postgres + auth + storage) | Sync engine; photo storage; row-level security |
| Maps | Mapbox (free tier) or react-native-maps | Color-coded school markers |
| Web dashboard | Next.js + Tailwind + Mapbox GL JS | Desktop view for ministry analysts |
| Charts | Chart.js | Score distribution histograms, trend lines |
| SMS fallback | Twilio API | Submit basic audit data via SMS when internet is unavailable |
| QR codes (optional) | react-native-qrcode-svg | Unique school ID for re-audits |
| Deployment | EAS Build (Expo) + Vercel (dashboard) + Supabase | All free tiers |

## Stakeholders

- **Ministries of Education** — need ground-truth data to allocate resources effectively
- **UNICEF, UNESCO, World Bank** — rely on school data for global education indicators (SDG 4)
- **Local advocacy groups** (e.g., Aktion, Code for Africa, Education International)
- **Investigative journalists** covering education infrastructure gaps
- **Parent-teacher associations** — want to advocate for their school with evidence
- **School heads** — want to report honestly without fear of penalty

## Why This Is Hackathon-Sized

- **No AI** — checklist-based data collection with straightforward math for scoring
- **Offline-first is a solved pattern** — SQLite + sync is well-documented and widely open-sourced
- **Checklist is fixed** — the audit is a predefined list of questions; no NLP or image processing
- **One-school-at-a-time** — each audit is independent; no complex graph or relationship modeling
- **React Native + Supabase** is a battle-tested stack for offline-first data collection apps
- **SMS fallback is simple** — structured text input parsed by the server; 3 days of work

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | App scaffold + school profile creation | React Native project; GPS capture; photo + form; offline SQLite |
| Week 2 | Resource checklist + scorecard | All audit fields; auto-compute score (0–100) with sub-scores |
| Week 3 | Sync + web dashboard | Supabase sync; Next.js map dashboard with color-coded markers |
| Week 4 | Government comparison view | Side-by-side EMIS vs. ground-truth; filter by district |
| Week 5 | SMS fallback + multi-language | Submit basic audit via SMS; add English + 1 local language |
| Week 6 | Polish and pilot pack | CSV export, per-school scorecard PDF, onboarding materials for 1 district |

## Monetization

| Model | Details |
|---|---|
| B2G (Ministry of Education) | $30,000–$100,000 per country for national deployment + training |
| Donor/NGO program | UNICEF, UNESCO, World Bank education programs: $50K–$200K per country |
| District-level SaaS | $5,000–$15,000 per district per year for dashboard + analytics |
| Media/advocacy license | Free for journalists and advocacy groups (builds visibility and pressure for government adoption) |

**Target:** Pilot in 2 districts with a local advocacy partner; use ground-truth gaps to drive media coverage and ministry interest.

## Long-Term Vision

A global public good: the most comprehensive ground-truth dataset on school resources ever assembled. Every school in every country has a transparent, publicly verifiable resource profile. Donors and ministries allocate budgets based on actual needs, not political convenience. Parents can see exactly what their child's school has and advocate for the rest. The comparison engine becomes a national accountability tool — no ministry can claim "all schools electrified" when the map shows otherwise.

## Risks

| Risk | Mitigation |
|---|---|
| Government hostility to ground-truth data | Keep platform independent; work through media and civil society; compare vs. government own published data (hard to argue with your own numbers) |
| School heads penalized for honest reporting | Anonymize school head identity; publish only school-level data |
| Audit frequency / sustainability | Design for quarterly re-audit in 10 minutes; gamify with leaderboards; partner with school clubs and parent groups |
| Data quality / inconsistent audits | Structured checklist constrains variability; mandatory photo evidence for key items (toilet, electricity, water); random spot-check verification |
| Low connectivity | Offline-first + SMS fallback + batch sync; single audit produces < 500KB of data |
