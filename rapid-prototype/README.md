# ⚡ Rapid Prototypes

**11 non-AI ideas** that can be built solo in 2-6 weeks — zero AI, zero computer vision, maximum impact.

---

## Why This Track

Not every real-world problem needs AI. Some of the highest-impact tools are **pure data engineering, CRUD, maps, messaging, and workflow logic** — perfectly scoped for weekend hackathons, solo development, or first-time open-source contributors.

Each of these solves a pressing problem for **millions of underserved users** using technology that already works reliably.

## The Problems

| # | Problem | Type | Build Time | Difficulty | Impact |
|---|---------|------|-----------|------------|--------|
| 01 | [Village Grain Bank Manager](village-grain-bank-manager.md) | WhatsApp + CRUD + Inventory | 2-3 weeks | ★☆☆☆☆ | 500M+ smallholder farmers |
| 02 | [Medicine Stock Visibility](medicine-stock-visibility.md) | WhatsApp/SMS + Inventory | 2-4 weeks | ★☆☆☆☆ | 100K+ rural clinics |
| 03 | [Infrastructure Defect Reporter](infrastructure-defect-reporter.md) | Maps + Workflow + Escalation | 3-4 weeks | ★★☆☆☆ | 500+ city governments |
| 04 | [Procurement Data Quality Monitor](procurement-data-quality-monitor.md) | Data Pipeline + Dashboard | 3-4 weeks | ★★☆☆☆ | 50+ country transparency |
| 05 | [Informal Worker Skills Passport](informal-worker-skills-passport.md) | Offline Mobile + QR + Verification | 4-6 weeks | ★★★☆☆ | 15-20M informal workers |
| 06 | [School Resource Transparency Map](school-resource-transparency-map.md) | Offline Forms + Maps + Dashboards | 4-6 weeks | ★★★☆☆ | 100K+ schools tracked |
| **07** | [Annapurna — PDS Tracker](annapurna-pds-tracker.md) | WhatsApp + Maps + API Integration | 4-6 weeks | ★★★☆☆ | 800M PDS beneficiaries |
| **08** | [RathLink — Waste Worker Platform](rathlink-waste-worker-platform.md) | QR + Offline Mobile + Ledger | 4-6 weeks | ★★★☆☆ | 1.5M informal waste workers |
| **09** | [BhuLekh — Land Records App](bhulekh-land-records-app.md) | API Search + Maps + Documents | 3-4 weeks | ★★☆☆☆ | 200M+ landholding households |
| **10** | [Setu — Government Form Assistant](setu-government-form-assistant.md) | Form Engine + DigiLocker + Workflow | 3-4 weeks | ★★☆☆☆ | 1.4B Indian citizens |
| **11** | [JalSathi — Water Testing Network](jalsathi-water-testing-network.md) | Maps + SMS + Crowdsourcing | 4-6 weeks | ★★★☆☆ | 100M+ exposed to contaminated water |

## Quick Start

| Time Available | Pick This |
|---------------|-----------|
| **24-48 hour hackathon** | [Village Grain Bank Manager](village-grain-bank-manager.md) or [Medicine Stock Visibility](medicine-stock-visibility.md) |
| **Weekend + follow-up** | [Infrastructure Defect Reporter](infrastructure-defect-reporter.md) or [Procurement Data Quality Monitor](procurement-data-quality-monitor.md) |
| **4-6 week sprint** | [Informal Worker Skills Passport](informal-worker-skills-passport.md) or [School Resource Transparency Map](school-resource-transparency-map.md) |
| **India civic sprint** | [BhuLekh](bhulekh-land-records-app.md) (3-4w) or [Setu](setu-government-form-assistant.md) (3-4w) — state API integration |

## Tech Stack Patterns

Most of these use the same proven stack:
- **Backend:** Node.js / Python + PostgreSQL + Supabase
- **Messaging:** Twilio WhatsApp Business API + SMS
- **Mobile:** React Native (offline-first with SQLite)
- **Maps:** Mapbox / Leaflet
- **Auth:** Supabase Auth or simple phone-based

## Why No AI?

These problems are intentionally AI-free:
1. **Lower barrier to entry** — Pure engineering, no ML expertise needed
2. **More reliable** — Deterministic systems for life-critical inventory/health data
3. **Faster to ship** — No model training, no data collection pipeline
4. **Offline-first** — Runs where internet is unreliable
5. **Rapidly prototypeable** — Cursor/Claude can scaffold the entire app in one session

## Monetization Patterns

All follow **open-core models**:
- **Free** — For end-users (farmers, workers, citizens)
- **Paid** — B2G (governments), B2B (NGOs, ethical employers)
- **Range** — $10-200K/year per entity
