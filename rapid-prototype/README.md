# ⚡ Rapid Prototypes

**6 non-AI ideas** that can be built solo in 2-6 weeks — zero AI, zero computer vision, maximum impact.

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

## Quick Start

| Time Available | Pick This |
|---------------|-----------|
| **24-48 hour hackathon** | [Village Grain Bank Manager](village-grain-bank-manager.md) or [Medicine Stock Visibility](medicine-stock-visibility.md) |
| **Weekend + follow-up** | [Infrastructure Defect Reporter](infrastructure-defect-reporter.md) or [Procurement Data Quality Monitor](procurement-data-quality-monitor.md) |
| **2-3 week sprint** | [Informal Worker Skills Passport](informal-worker-skills-passport.md) or [School Resource Transparency Map](school-resource-transparency-map.md) |

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
