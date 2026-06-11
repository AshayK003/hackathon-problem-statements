---
track: rapid-prototype
status: published
---

# Rural Medicine Stock Visibility Platform

> **Category:** Public Health | Supply Chain
> **Build time:** 2–4 weeks (solo developer)

## The Problem

Rural clinics across Africa and Asia regularly run out of essential medicines — malaria treatments, antibiotics, vaccines, maternal health supplies. The stockout isn't because the drugs don't exist; it's because nobody knows what's on the shelf until a patient dies and the news reaches the district capital.

Stock visibility is a one-way black hole. The central medical store sends shipments out, but has no real-time data on what actually arrived, what was dispensed, or what remains. District health officers rely on monthly paper reports that arrive weeks late or not at all. By the time a stockout is officially recorded, the clinic has been empty for days or weeks.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| Monthly paper reports to district office | 2–4 week delay; lost in transit; easily falsified |
| Spreadsheets on a single clinic computer | Power outages lose data; single point of failure |
| SMS-based reporting (manual) | No structure; staff forget; no escalation logic |
| National LMIS (Logistics Management Systems) | Expensive, complex, requires training; rarely reaches last-mile clinics |
| Nothing | Most common approach |

## What to Build

A **WhatsApp + SMS + USSD bot** where every Monday morning, a simple automated message asks the clinic in-charge to report stock levels for 5–10 critical medicines. The interaction takes under 2 minutes.

- **Weekly prompts** — automated reminder via the channel the clinic prefers (WhatsApp, SMS, or USSD)
- **Stock input** — report quantities received, dispensed, and remaining for each tracked medicine
- **Days of stock remaining** — auto-calculated based on consumption rate; flag when < 14 days
- **Escalation engine** — when stock of any medicine drops below threshold, auto-notify the district pharmacist, then the provincial supply officer, then the national LMIS coordinator
- **Dashboard** — web view for health administrators to see all clinics on a map, color-coded by stock status
- **Export** — CSV/PDF reports for government reporting requirements

No AI, no machine learning. Pure form logic + alerting math.

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Messaging | Twilio (WhatsApp + SMS + USSD) | Single API for all three channels; global reach |
| Backend | Node.js or Python (FastAPI/Flask) | Simple request-response; easy to deploy |
| Database | PostgreSQL | Reliable; good with time-series stock data |
| Frontend | Next.js + Tailwind CSS | Admin dashboard with map view |
| Maps | Leaflet (free, no API key needed) | Lightweight; clinic-level pin mapping |
| Cron/Scheduling | GitHub Actions (scheduled) | Free cron for weekly reminders |
| Deployment | Railway or Fly.io | Cheap single-container deploys |

## Stakeholders

- **100,000+** rural clinics across sub-Saharan Africa and South Asia
- **Ministries of Health** (district, provincial, national levels)
- **WHO, UNICEF, MSF** — supply chain partners and auditors
- **Global Fund, PEPFAR, Gavi** — funders who need stock visibility for their programs
- **Clinic in-charges** — nurses and medical officers who are the front line

## Why This Is Hackathon-Sized

- **No AI** — just conditional logic, math, and CRUD
- **Async by design** — no real-time sync needed; weekly batch updates work fine
- **Multi-channel but one code path** — Twilio abstract the channel; same backend for WhatsApp/SMS/USSD
- **Fixed scope** — exactly 5–10 medicines per country; data model is tiny
- **Proven pattern** — the "weekly check-in" bot is a well-understood interaction design

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | Data model + Twilio webhook | Receive and store stock reports via WhatsApp and SMS |
| Week 2 | Days-of-stock math + alerts | Calculated thresholds; auto-escalation to district level |
| Week 3 | Admin dashboard | Map view, per-clinic history, CSV export, alert management |
| Week 4 | Scheduled reminders + polish | GitHub Actions cron for Monday prompts; onboarding flow for new clinics |

## Monetization

| Model | Details |
|---|---|
| B2G country licensing | $20,000–$100,000 per country per year, depending on clinic count |
| Multi-country deployment | WHO/UNICEF regional contracts at $50,000–$250,000/year |
| Donor-funded pilots | Global Fund and Gavi fund stock visibility pilots; typical budget $50K–$200K |

**Target:** Pilot in 1 district (20–50 clinics) for 3 months, then pitch to Ministry of Health.

## Long-Term Vision

A full national essential medicines visibility system covering all public health facilities. Integration with national LMIS for automated reorder triggers. Expansion to consumables (syringes, gloves, diagnostics) and cold-chain monitoring. A continental dashboard where the Africa CDC can see stock levels at every clinic from Cape Town to Cairo.

## Risks

| Risk | Mitigation |
|---|---|
| Staff don't respond to weekly prompts | Three reminders (WhatsApp, SMS, voice call fallback); escalate to supervisor after 2 missed weeks |
| Phone/SIM card changes | Train one designated clinic phone; allow simple number update via USSD |
| Data quality (falsified reports) | Cross-check with dispensing records; random SMS audits |
| Power / network outages | USSD works without data; queue reports; backfill when connected |
| Government procurement cycles | Start with donor funding (Global Fund, Gates, Gavi) before chasing ministry budgets |
