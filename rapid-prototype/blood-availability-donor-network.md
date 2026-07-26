---
track: rapid-prototype
status: published
---

# Real-Time Blood Availability & Donor Network

> **Category:** Public Health | Health Supply Chain (India)
> **Build time:** 4–6 weeks (solo developer)

## The Problem

India faces a blood shortage of over 1 million units annually. The National Blood Transfusion Council (NBTC) estimates that the country requires 14-15 million units of blood every year, but only 13-13.5 million units are collected. The gap isn't primarily a collection problem — it's a logistics and information problem. On any given day, one hospital is cancelling surgeries because they can't find O-negative blood, while another hospital 5 km away has 20 units expiring on the shelf.

The Indian government operates e-RaktKosh, a centralised blood bank management system covering most government blood banks. In theory, it provides real-time inventory. In practice, adoption among private blood banks is low, the system lacks a citizen-facing interface for finding blood by location and type, and there is no donor-side engagement at all — no way for a volunteer donor to say "I'm available to donate, here's my blood type and location." The result is a system where hospitals, blood banks, and donors operate in parallel silos, and emergency searches for rare blood types devolve into frantic WhatsApp group messages and social media pleas.

## Current Solutions and Limitations

| Approach | Limitations |
|----------|-------------|
| e-RaktKosh (MoHFW) | Government blood banks only; no citizen interface; no donor directory |
| Social media/X posts for emergency blood | Unverified, uncoordinated, one-off; no systematic matching |
| WhatsApp groups for blood donors | Fragmented by city and group admin; stale contact lists; spam |
| Individual hospital blood banks | No cross-hospital visibility; patient must call each hospital separately |
| Paid blood finder services | Small coverage area; not transparent about inventory; exploitative pricing |
| Blood donation camp schedules | Static announcements; no way to notify donors when camp is happening nearby |

## What to Build

- **Real-time blood inventory aggregator**: Compile availability data from e-RaktKosh (where API is accessible), hospital blood banks (manual upload UI), and partner NGOs — unified view showing blood type × component stock by location
- **Emergency search**: "Find A-negative platelets within 10 km right now" — searchable by blood type, component, distance, and freshness
- **Donor directory with opt-in**: Donors register their blood type, location, and availability; receive SMS/WhatsApp alerts when their type is needed nearby
- **Camp calendar + notification**: NGOs and blood banks post upcoming donation camps; donors get notified when a camp is within their area and their blood type is in demand
- **Hospital-to-hospital transfer assistant**: Help hospitals identify nearby facilities with surplus stock of the needed type for inter-hospital transfers
- **WhatsApp bot**: "Hi, I need AB+ whole blood in Dadar. Who has it?" — the bot returns nearest inventory + camp schedule + donor contacts (with consent)

## Tech Stack

| Component | Choice | Why |
|-----------|--------|-----|
| Backend | Python FastAPI | Lightweight, async, great for SMS and WhatsApp integrations |
| Database | PostgreSQL | Relational integrity for inventory tracking; spatial queries via PostGIS |
| Frontend | React + Leaflet | Interactive map of blood banks, camps, and donor density |
| Messaging | Twilio WhatsApp + SMS API | Reach users on WhatsApp (primary) with SMS fallback for feature phones |
| Inventory sync | GitHub Actions (scheduled) + e-RaktKosh scraping | Hourly inventory refresh; no always-on server needed |
| Auth | Phone OTP (Twilio Verify) | Matches user base; no email/password friction |

## Stakeholders

- **14-15 million** units of blood required annually in India
- **3,000+** licensed blood banks (govt + private)
- **National Blood Transfusion Council (NBTC)** and State Blood Transfusion Councils
- **Indian Red Cross Society** and NGO blood donation organisers
- **Hospital transfusion departments** in 30,000+ hospitals
- **Voluntary blood donors** (estimated 10M+ regular donors)
- **Patients with thalassemia, haemophilia, cancers** — regular transfusion dependents

## Why This Is Hackathon-Sized

- **No AI** — all logic is CRUD + search + notification workflows
- **Well-defined data model** — blood banks, donors, camps, inventory are simple entities
- **e-RaktKosh provides anchor data** — start with government banks, expand to private
- **WhatsApp bot interface** — most Indian users already have WhatsApp; no app install required
- **Proven notification pattern** — Twilio SMS broadcast for donor alerts is well-documented
- **Clear success metric** — "units of blood that would have expired but were transferred to a hospital that needed them"

## MVP Timeline

| Week | Focus | Deliverable |
|------|-------|-------------|
| Week 1 | e-RaktKosh data ingestion + inventory DB | Scheduled scraper/API integration for government blood banks; unified inventory table |
| Week 2 | Search + map interface | Web app to search blood by type and location; show results on map with distance and last-updated time |
| Week 3 | WhatsApp bot for search | Users message a WhatsApp number → bot returns nearby inventory; SMS fallback for feature phones |
| Week 4 | Donor registration + camp calendar | Donors register via WhatsApp; camps show on map; notification when camp is nearby |
| Week 5 | Hospital transfer match + emergency alerts | Inventory matching between hospitals; emergency alert broadcast to registered donors (via WhatsApp/SMS) |
| Week 6 | Testing + pilot onboarding | Onboard 2-3 blood banks and 1 NGO partner; field test donor registration flow |

## Risks

| Risk | Mitigation |
|------|------------|
| e-RaktKosh data may be incomplete or stale | Cache with timestamps; show "last updated X hours ago" on each inventory entry; degrade gracefully |
| Private blood banks may not share inventory data | Offer read-only public link for easy upload; frame as "visibility brings more donors to your bank" |
| Donor privacy and consent management | Explicit opt-in; donors control notification radius and frequency; data deletion on request |
| Blood type verification for donors | Display as self-reported with disclaimer; encourage verification at first donation |
| Emergency use case attracts non-emergency queries | Separate flow: emergency SOS triggers SMS to top donors; standard queries use WhatsApp response within 60 seconds |
