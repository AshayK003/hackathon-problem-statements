---
track: rapid-prototype
status: published
---

# BhuLekh — Land Record Access Interface

> **Category:** Land Governance | Property Rights (India)
> **Build time:** 3–4 weeks (solo developer)

## The Problem

Under the Digital India Land Records Modernization Programme (DILRMP), the government has spent over a decade digitizing India's rural land records. Today, an estimated 95% of Records of Rights (RoR) and 68% of cadastral maps have been digitized — a massive data asset representing the property ownership of roughly 200 million rural households. Yet for ordinary citizens, actually accessing these records remains a frustrating, fragmented experience.

Each of India's 36 states and union territories operates its own land record portal with its own URL, login flow, language, data schema, and user interface. A farmer trying to verify the ownership of a plot in Maharashtra must navigate the MahaBhulekh portal, a person in Uttar Pradesh uses Bhulekh UP, and someone in Karnataka uses Bhoomi. There is no unified search, no plain-language summary, and no way to easily check if a property has pending litigation. For property buyers, the process of due diligence involves visiting multiple websites, cross-referencing surveys against cadastral maps, and manually checking court records — often requiring paid intermediaries.

Land disputes account for nearly two-thirds of all pending civil cases in Indian courts, and the inability of ordinary citizens to easily verify ownership is a major contributing factor. The data is already digitized and accessible via state APIs; what is missing is a unified, citizen-friendly interface that makes these records truly accessible.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| State land record portals (MahaBhulekh, Bhulekh UP, Bhoomi, etc.) | Each state has separate portal, UX, and language; poor mobile experience; no cross-state search |
| DocXplorer / Attentive.ai | Enterprise AI for digitizing land records; not a consumer-facing search tool |
| NoBroker / Housing.com | Urban property listings only; no rural land record access or ownership verification |
| Zebi blockchain pilot | Limited to Andhra Pradesh pilot; not consumer-facing; not integrated with state portals |
| Property lawyers / intermediaries | ₹500–₹5,000 per search; slow; no transparency in the process itself |

## What to Build

- **Unified search** — Single search box (name + village + district) that queries land records across multiple states simultaneously
- **Plain-language property summary** — Translate government-formatted RoR data into a simple, readable card: owner name, survey number, area, type of land, irrigation status, current encumbrances
- **Dispute checker** — Plug into eCourts API to display any pending litigation associated with a specific plot or owner name
- **Document download** — One-click download of RoR (Record of Rights), mutation certificate, and other registered documents
- **Property history timeline** — 30-year chain of ownership transfers where available from state records
- **Map overlay** — Display survey number boundaries on a cadastral map overlaid on satellite imagery for visual verification
- **Buying guide** — Step-by-step checklist for verifying a property before purchase, customized to the specific state's requirements
- **Mutation pending alert** — Subscribe to a notification that fires when a mutation application is filed against a property you care about

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Backend | Python FastAPI | Excellent HTTP client ecosystem for calling 30+ state APIs; async by default |
| Database | PostgreSQL + PostGIS | Spatial queries for map overlay and survey-number-to-coordinate mapping |
| Frontend | Next.js + Tailwind + Leaflet | Server-side rendering for SEO; Leaflet for free map overlays |
| APIs | State land record portals + DILRMP + eCourts | All government-provided; scraping-free integration where possible |
| Auth | DigiLocker OAuth | Citizens already use DigiLocker for Aadhaar-based verification; seamless SSO |
| Caching | Redis | Cache state API responses to reduce load on government servers and improve response times |
| Deployment | Railway / AWS Lambda | Stateless backend; easy scaling to handle traffic spikes |

## Stakeholders

- **~200 million** rural land-owning households who need occasional record access
- **500 million+** citizens who need to verify a land record at least once per year (buyers, sellers, heirs)
- **Property buyers, realtors, and lawyers** — currently paying intermediaries for manual verification
- **Banks and financial institutions** — need land record verification for loan processing and mortgage approval
- **State Revenue Departments** — already maintain the underlying data; benefit from reduced counter inquiries
- **eCourts system** — integration could reduce land dispute filings by improving pre-purchase due diligence

## Why This Is Hackathon-Sized

- **All data already digitized** — no data collection or OCR needed; just API integration and UI work
- **36 state APIs but one interface** — each state API is different, but the output schema is similar; adapter pattern solves this
- **Zero ML needed** — no document parsing, no image recognition, no prediction models
- **Simple search + display** — core UX is a search box and a results card; complex only in API variety, not in logic
- **Well-understood domain** — land record verification is a solved problem in other countries; India just lacks a unified interface

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | Unified search across 3 pilot states (Maharashtra, Karnataka, UP) | Single search box returns RoR data from all three states; API adapter layer built |
| Week 2 | Plain-language property summary + dispute check | RoR data rendered as readable card; eCourts API integration for pending cases |
| Week 3 | Document download + DigiLocker integration | Download RoR/mutation certificate; OAuth login via DigiLocker |
| Week 4 | Property transfer checklist + polish | Buying guide, map overlay for survey numbers, mutation alert subscription |

## Monetization

| Model | Details |
|---|---|
| Freemium | Free for basic record search (up to 5/month); ₹50 per verified detailed report |
| B2B bank API access | ₹5–₹20 lakh per year for high-volume API access (loan processing, title verification) |
| B2G licensing | ₹10–₹30 lakh per state per year for customized dashboards and bulk access |
| Transaction fee | Small percentage on property transactions where platform is used for verification |

**Target:** Free for individual citizens; paid plans for banks, realtors, and bulk users.

## Long-Term Vision

"India's Zillow for rural land" — a single destination where any citizen can look up any plot of land in India and instantly see who owns it, what its history is, whether it has disputes, what taxes are due, and what its fair market value is. Integration with banks for instant loan approval, with registrars for mutation tracking, and with the court system for dispute resolution. Transparency in land records reduces litigation, unlocks credit for rural households, and makes property transactions faster and fairer.

## Risks

| Risk | Mitigation |
|---|---|
| State API changes and availability issues | Abstract all state integrations behind a unified adapter layer; cache aggressively; graceful fallback with stale data |
| "95% digitized" does not mean 95% accurate | Always show data source and date; add disclaimer that records may contain errors; invite corrections |
| Language diversity across 22+ scheduled languages | Start with Hindi + 8 regional languages covering 90% of users; community translations for the rest |
| Political sensitivity around land data | Frame as citizen empowerment and convenience; work with state revenue departments on data-sharing MoUs |
| Low digital literacy in rural areas | Provide assisted access via CSC (Common Service Centre) network; WhatsApp-based query option in Phase 2 |
