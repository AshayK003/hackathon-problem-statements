---
track: rapid-prototype
status: published
---

# RathLink — Informal Waste Worker Platform

> **Category:** Waste Management | Circular Economy (India)
> **Build time:** 4–6 weeks (solo developer)

## The Problem

India's informal waste picking workforce — estimated at 1.5 million people and growing — is the invisible engine behind the country's recycling industry. These workers collect, sort, and channel an estimated 70% of all plastic waste that gets recycled in India, saving municipalities billions in landfill costs and keeping millions of tonnes of material in the circular economy. Yet they remain entirely outside the formal economy: no digital identity, no bank account, no health insurance, no minimum wage protection, and no bargaining power.

The kabadiwala (scrap dealer) system that intermediates between waste pickers and recyclers is cash-based, fragmented, and deeply exploitative. Middlemen routinely take 40–50% margins, leaving workers with ₹200–400 per day for backbreaking labour that involves walking 6–7 kilometres carrying 20–40 kg of waste. Without a digital record of their work, pickers cannot prove their income to qualify for government schemes, cannot access credit, and cannot organize collectively to demand better prices.

The technology to fix this exists — digital identity, basic ledger accounting, and peer-to-peer marketplaces are all solved problems. What is missing is a platform designed around the specific constraints and needs of India's informal waste workers.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| Plastics For Change | Brand-facing platform for sourcing recycled plastic; does not serve workers directly |
| Kabadiwala Connect | WhatsApp-based scrap buying for consumers; workers still have no identity or ledger |
| SWaCH Pune cooperative | Exemplary model but non-tech and location-specific; not replicable at scale |
| Municipal helplines / apps | None designed for waste pickers; focus on citizen complaints, not worker empowerment |
| Nothing (majority) | No digital presence at all; workers operate entirely in the informal cash economy |

## What to Build

- **Digital worker ID** — QR-coded card with name, photo, phone, waste-type specialties, and a verifiable work history
- **Collection tracker** — Daily log of waste collected (weight by type — plastic, metal, paper, glass) with photo proof
- **Earnings ledger** — Transparent transaction record showing every sale, the price paid, the buyer, and the calculated margin
- **Health & safety module** — PPE request form, nearest health camp locator, insurance linkage (PMJAY, PMSYM schemes)
- **Market price board** — Real-time scrap rates for different materials across local kabadiwala depots so pickers can compare
- **Scrap yard map** — Map of registered kabadiwala and recycler depots with user-reported ratings and pricing
- **Group formation** — Tool for workers to form informal cooperatives for bulk bargaining power
- **Scheme linkage** — Guided flow to apply for government schemes: PMJAY (health insurance), PMSYM (social security for informal workers), Jan Dhan (bank account)

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Backend | Node.js / Python FastAPI | Fast development; well-suited for CRUD + messaging workflows |
| Database | PostgreSQL (server) + SQLite (offline) | SQLite enables full offline operation on the mobile device; syncs when online |
| Frontend | React Native (offline-first) | Cross-platform mobile app that works without internet for core functions |
| Messaging | Twilio WhatsApp API | Workers already use WhatsApp; no app install barrier |
| QR Codes | qrcode library (Node.js/Python) | Simple, proven technology for worker identification cards |
| Mapping | Leaflet (OpenStreetMap) | Free mapping for scrap yard locations and worker routes |
| Deployment | Railway / Vercel + Play Store (APK) | Low-cost hosting for backend; APK sideloading for phones without Play Store |

## Stakeholders

- **1.5 million+** informal waste pickers across Indian cities (conservative estimate; actual likely higher)
- **100,000+** kabadiwala scrap depots in urban and peri-urban areas
- **3,500+** registered recyclers who buy processed scrap
- **Municipal Solid Waste Management departments** — responsible for collection targets and Swachh Bharat metrics
- **Brands with EPR obligations** — required under Plastic Waste Management Rules to track their packaging waste
- **NGOs and social enterprises** — working on waste worker welfare (Chintan, Hasiru Dala, Saahas)

## Why This Is Hackathon-Sized

- **Zero ML** — no image recognition, no predictive models, no NLP
- **QR + CRUD = core** — the entire app is identity management, ledger entry, and map display
- **Offline-first mobile** — proven pattern; SQLite sync is well-documented
- **Fixed identity pattern** — worker registration flows are standard; DigiLocker and Aadhaar APIs handle verification
- **Deterministic scope** — each feature (collection log, price board, health camp) is independently buildable

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | Worker registration + QR code generation | Registration form, printable QR card, basic worker profile page |
| Week 2 | Daily collection log | Add collection entry (weight, type, photo), sync to server, view history |
| Week 3 | Scrap price board + earnings dashboard | Real-time prices from 50+ depots; worker sees daily/weekly/monthly earnings |
| Week 4 | Health insurance linkage flow | Guided PMJAY application; nearby health camp locator on map |
| Week 5 | WhatsApp integration | Daily earnings summary via WhatsApp; price alerts for specific materials |
| Week 6 | Cooperatives + group formation | Group creation, collective bargaining request, bulk sale posting |

## Monetization

| Model | Details |
|---|---|
| B2B recycling data | ₹50,000–₹2,00,000 per year per recycler for verified sourcing data and EPR compliance reports |
| CSR funding | ₹20 lakh–₹1 crore per year from corporate CSR budgets for waste worker welfare programs |
| B2G municipal compliance | Dashboard and API for municipalities to track informal sector integration under Swachh Bharat |
| Open-core (free for workers) | All worker-facing features always free; institutional users pay for data and analytics |

**Target:** Pilot with 1 city (500 workers, 20 depots, 5 recyclers) before expanding to 10 cities.

## Long-Term Vision

"LinkedIn + QuickBooks for India's recycling workforce" — every informal waste picker has a portable digital identity, a verifiable earnings history, and access to health insurance, credit, and cooperative bargaining power. Municipalities and brands get transparent, auditable data on where their waste goes and who recovers it. India's circular economy becomes inclusive, formal, and dignified for the workers who power it.

## Risks

| Risk | Mitigation |
|---|---|
| Worker literacy levels vary widely | Icon-based UI with minimal text; voice-guided input and Hindi/bilingual options |
| Middlemen/landlords may oppose worker empowerment | Cooperative model first (workers organized = more leverage); partner with existing unions |
| Health insurance scheme integration is complex | Integrate via government APIs only; provide assisted application flow through NGO partners |
| Monetizing from workers is impossible | Never charge workers; all revenue is B2B (recyclers, brands, CSR, government) |
| Smartphone ownership not universal | WhatsApp-first for basic operations (registration, earnings check); app for richer features |
