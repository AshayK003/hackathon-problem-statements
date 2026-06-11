---
track: rapid-prototype
status: published
---

# Annapurna — PDS Supply Chain Tracker

> **Category:** Food Security | Public Distribution System (India)
> **Build time:** 4–6 weeks (solo developer)

## The Problem

India's Public Distribution System (PDS) covers over 800 million beneficiaries through more than 500,000 Fair Price Shops (FPS), distributing 52 million tonnes of food grain every year. Yet an estimated 28% of this grain never reaches its intended recipients — roughly 20 million tonnes worth ₹69,108 crore in leakage. Ghost beneficiaries, black-market diversion of subsidized grain, and arbitrary pricing at the shop level are rampant, and the poorest citizens bear the cost.

Despite decades of digitization under the government's ePDS initiative, there is no public-facing tool that lets a citizen find out where their grain is, when it will arrive at their local shop, or whether the price being charged matches the legally mandated rate. The data exists — siloed inside state food department servers — but it is invisible to the 800 million people it is meant to serve. Families show up at their FPS on distribution day only to be told "no stock" or to face arbitrary markups they cannot verify.

The result is systemic leakage that erodes trust in the system and wastes public money at a scale that dwarfs most other welfare programs. Building a transparent, citizen-facing tracker is a pure data-engineering problem with the potential to recover billions of rupees in lost grain every year.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| ePDS portals (state-level) | Internal government dashboards; not citizen-facing; no per-shop stock or pricing visibility |
| PDS analytics dashboards | Aggregate state-level reports; useless for an individual trying to buy rice today |
| State food department websites | Fragmented across 36 states; poor UX; typically broken or outdated |
| WhatsApp/social media channels | Unofficial, fragmented, unverified information |
| Nothing | Majority of beneficiaries have no way to check stock or prices before visiting the shop |

## What to Build

- **FPS locator map** — Find the nearest Fair Price Shop with directions, opening hours, and contact details
- **Grain-in-transit visualizer** — Trace a shipment from FCI godown → state warehouse → district depot → local FPS with ETA
- **Ghost beneficiary reporter** — Flag suspicious accounts (same phone number across multiple families, deceased persons still on rolls)
- **Price checker** — Enter a shop ID and see the official price (rice ₹3/kg, wheat ₹2/kg) vs. what the shop is actually charging (crowdsourced)
- **Stock availability indicator** — Green/Yellow/Red badges for each FPS based on current inventory levels
- **Distribution calendar** — Per-shop schedule showing when the next distribution is due
- **Complaint form** — File a formal complaint directly to CPGRAMS (Centralized Public Grievance Redress and Monitoring System) from within the app

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Backend | Node.js / Python FastAPI | Fast development; large ecosystem for data scraping and API integration |
| Database | PostgreSQL | Relational integrity for financial-grade transaction tracking |
| Frontend | Next.js + Tailwind CSS | Server-side rendering for SEO; rapid UI iteration |
| Maps | Leaflet (OpenStreetMap) | Free, no API key needed; works offline with tiles |
| Messaging | Twilio WhatsApp Business + SMS | Reach beneficiaries on their existing messaging platform; SMS fallback for feature phones |
| Data pipeline | GitHub Actions (cron) | Daily scraping of state PDS portals; no infrastructure to manage |
| Auth | Phone number OTP (Twilio Verify) | Matches literacy and access patterns of target users |

## Stakeholders

- **800 million** PDS beneficiaries across India
- **500,000+** Fair Price Shop dealers and their families
- **36** state Food and Civil Supplies departments
- **Food Corporation of India (FCI)** — central procurement and distribution agency
- **NGOs and advocacy groups** — Right to Food Campaign, PUCL, Centre for Equity Studies
- **Media and transparency activists** — tracking welfare leakage

## Why This Is Hackathon-Sized

- **Zero AI** — all logic is deterministic: API scraping, CRUD operations, conditional alerts
- **Fixed scope** — one government program, one data model, one user journey
- **Maps + CRUD only** — no complex algorithms, no real-time collaboration, no video or image processing
- **Proven Twilio pattern** — WhatsApp bots for government service delivery are well-documented
- **Data already exists** — the challenge is aggregation and presentation, not generation or modeling

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | FPS locator map + API integration for 3 states | Interactive map showing all FPS locations with basic info from state portals |
| Week 2 | Grain-in-transit visualization | Tracking view for 3 pilot states showing shipment movement from FCI to FPS |
| Week 3 | Stock checker + price reporter | Per-shop stock indicator and crowdsourced price verification with moderation |
| Week 4 | SMS alerts + complaint routing | Daily SMS with distribution schedule; one-click complaint filing to CPGRAMS |
| Week 5 | Expand to 10 states + polish | Onboarding for additional states, bug fixes, load testing |
| Week 6 | Stakeholder outreach + launch | Deploy on Railway/Vercel; onboard NGO partners for field testing |

## Monetization

| Model | Details |
|---|---|
| B2G state licensing | ₹10–50 lakh per state per year for customized dashboards and API access |
| NGO partnerships | ₹5–20 lakh per year for white-label versions used in advocacy campaigns |
| Open-core (free for citizens) | Core tracker always free; premium analytics and reports for institutional users |
| CSR funding | Corporate social responsibility grants for transparency and governance projects |

**Target:** Pilot with 3 states (free), then sell B2G licenses to remaining states.

## Long-Term Vision

"Where's My Grain" for India — a comprehensive public goods transparency platform that crowds out leakage through visibility. Every grain movement from farm gate to family kitchen is tracked, every price is verified, and every ghost beneficiary is flagged. The platform becomes the de facto public interface for India's largest welfare program, empowering citizens with the information they need to claim what is rightfully theirs.

## Risks

| Risk | Mitigation |
|---|---|
| State data availability varies widely — some portals are unmaintained | Abstract all portal integrations behind a unified API adapter layer; gracefully degrade for states with broken APIs |
| FPS dealers may oppose price transparency features | Frame as a tool for dealers too (stock management, demand forecasting); partner with honest dealers as champions |
| Low smartphone adoption in rural areas | SMS-first interface for querying stock and prices; WhatsApp for richer interaction |
| Government portals change frequently | CI/CD pipeline that alerts on scraping failures; manual fallback with cached data |
| Hostile government response to transparency | Maintain strict legal compliance; frame as citizen empowerment, not watchdog activism |
