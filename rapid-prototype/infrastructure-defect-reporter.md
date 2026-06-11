---
track: rapid-prototype
status: published
---

# Public Infrastructure Defect Reporter & Escalation Tracker

> **Category:** Infrastructure | Civic Tech
> **Build time:** 3–4 weeks (solo developer)

## The Problem

In most developing countries, when a road collapses, a streetlight dies, a water pipe bursts, or a school toilet overflows, there is no channel for citizens to report it and no way to track whether the government has even acknowledged the issue, let alone fixed it.

The typical process is: a citizen tells a local ward councillor (who may or may not write it down), the councillor tells a municipal office (which may or may not log it), and the paper report disappears into a file cabinet. Months later, if a journalist or activist makes enough noise, something might happen.

Citizens have no way to hold anyone accountable. Public works departments have no way to prioritize across hundreds of scattered complaints. The lack of a structured, transparent pipeline means small problems fester into expensive emergencies.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| Call the municipal hotline (if one exists) | Busy signal; no ticket number; no follow-up possible |
| Tell a ward councillor | No paper trail; political favoritism |
| Social media (Twitter/Facebook) | Shouting into the void; no structured handoff to government |
| Community WhatsApp groups | Messages lost in chat; no escalation workflow |
| Paper complaint registers at municipal offices | "Lost"; deliberately slow-walked; no citizen visibility |

## What to Build

A **WhatsApp + web platform** where any citizen can report a public infrastructure defect and track its repair from submission to sign-off.

**Submission flow (WhatsApp):**
- Send a photo, a location (GPS share or text description), and a category (road, water, power, sanitation, school)
- Bot creates a ticket with a unique ID and confirms via WhatsApp
- Ticket is auto-routed to the responsible government department based on category + location

**Escalation engine (state machine):**
- **Day 0:** Ticket submitted → routed to department
- **Day 3:** No acknowledgment → auto-escalate to department head + district administrator
- **Day 7:** No progress update → auto-escalate to mayor / commissioner + publish as "stalled" on public dashboard
- **Day 14:** No resolution → public shame: auto-post to a public Twitter/X feed with photos and department name
- **Completion:** Citizen receives a verification code; enters it to confirm fix; ticket closed

**Web dashboard:**
- Public map of all open/resolved/stalled defects
- Department-level performance scores (average time to acknowledge, average time to fix)
- Per-ticket timeline visible to anyone with the ticket ID

No AI. Pure state machine + escalation rules + civic accountability math.

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Messaging | Twilio WhatsApp API | Broad reach; citizen friendly |
| Frontend | Next.js + Tailwind CSS | Dashboard + public map |
| Maps | Leaflet + OpenStreetMap tiles | Free, no API key |
| Backend | Next.js API routes + state machine library | Co-located; simple workflow engine |
| Database | PostgreSQL | Ticket state, escalations, audit log |
| Cron / Scheduler | GitHub Actions or Inngest | Daily tick for escalation checks |
| Social | Twitter/X API v2 (free tier) | Public shame automation |
| Deployment | Vercel + Supabase | Free tier covers medium city |

## Stakeholders

- **500+** city governments in Africa, Asia, and Latin America
- Citizens and resident welfare associations
- Municipal public works departments
- Anti-corruption watchdogs and civil society organizations
- Local media and investigative journalists
- Development partners (World Bank, UN-Habitat, Cities Alliance)

## Why This Is Hackathon-Sized

- **Fully deterministic** — state machines are well-understood; no AI, no ML, no probabilistic outputs
- **Single-city deploy** — deploy for one city at a time; no multi-tenant scaling complexity
- **WhatsApp-first** — citizens don't download an app; the bot is the UI
- **Reusable pattern** — the escalation engine is generic; category tiers and timelines are config
- **Public shaming = free marketing** — the stalled-defect Twitter feed drives adoption and press coverage

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | Ticket data model + WhatsApp intake | Citizen submits photo/location/category → ticket created with ID |
| Week 2 | State machine + escalation engine | Auto-escalation at days 3, 7, 14; status transitions |
| Week 3 | Admin interface + public dashboard | Department view to manage tickets; public map of defects |
| Week 4 | Completion verification + Twitter shame feed | Citizen confirmation flow; auto-posting stalled tickets |

## Monetization

| Model | Details |
|---|---|
| Municipal SaaS | $1,000–$5,000/year per city for medium cities; $10K+ for metros |
| B2G (national rollout) | $50,000–$150,000 per country for deployment + training |
| Foundation / donor funding | Civic tech grants from Omidyar, Luminate, Gates, World Bank GovTech |

**Target:** Deploy in 1 secondary city (500K–2M population) free for 6 months as pilot and impact case study.

## Long-Term Vision

A global open-source civic infrastructure accountability platform, deployed in hundreds of cities. Cross-department analytics showing which agencies are responsive and which are bottlenecks. Integration with procurement systems (see: Open Procurement Data Quality Monitor) to connect unrepaired defects to unspent maintenance budgets.

## Risks

| Risk | Mitigation |
|---|---|
| Government resistance / non-cooperation | Start with citizen-first model; make department routing configurable; publish data regardless |
| Low citizen smartphone penetration | USSD fallback for text-only reporting; toll-free number for voice |
| Fake / malicious reports | Phone number auth (OTP); rate-limit per user; require photo evidence |
| Political interference | Immutable ticket history; data export capability for civil society audits |
| Department capacity (no one to fix things) | Platform exposes capacity gaps — that's the point. Escalate to media and elected officials. |
