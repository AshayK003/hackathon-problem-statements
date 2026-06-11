---
track: us-civic-tech
status: published
---

# UtilityCoach — Energy Assistance & Efficiency Navigator

> 1 in 3 US households struggles to pay energy bills. LIHEAP has $3–5B/year to help — but 80% of eligible households never apply. Bridge the gap.

## The Problem

Energy poverty is a silent crisis in the wealthiest country on Earth. **1 in 3 US households** — over **48 million** — struggles to pay their energy bills. **33% of these households** report delaying medical care to afford utilities. Each winter and summer, stories emerge of seniors dying from heat or cold because they couldn't afford air conditioning or heating.

The federal Low Income Home Energy Assistance Program (LIHEAP) provides **$3–5 billion per year** to help — but **80% of eligible households never apply**. The reasons: fragmented state-by-state programs (50 states + DC + territories), confusing eligibility criteria, complex applications, short filing windows, and lack of awareness. By the time households learn about LIHEAP, they're often already in crisis — facing shut-off notices or living without power.

On top of LIHEAP, there's the Weatherization Assistance Program (WAP), utility-specific discount programs, state emergency assistance, and charitable funds — each with different applications, deadlines, and requirements. The system that's supposed to help is itself an access barrier.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| State LIHEAP websites | 50+ separate, confusing, non-standardized interfaces |
| 211 / social service hotlines | Overwhelmed; long waits; limited hours; can't file applications |
| Utility company assistance | Limited to bill payment plans; no LIHEAP or WAP help |
| Community action agencies | Underfunded; 4–6 week processing for appointments |
| Benefits enrollment platforms (e.g., Benefits.gov) | General, not energy-focused; no crisis intervention |

## What to Build

An energy assistance navigator that:

- **Screens for eligibility** — one form (income + state + household size) → all programs user qualifies for
- **Assists with applications** — step-by-step guidance through LIHEAP, WAP, utility discount, and state-specific programs
- **Tracks all deadlines** — application windows, recertification dates, shut-off moratoriums
- **Provides crisis intervention** — if user has a shut-off notice, generates hardship letter, finds emergency assistance, connects to utility disconnection prevention
- **Recommends efficiency measures** — low-cost changes, appliance rebates, weatherization programs
- **Generates appeal letters** — for denied or under-awarded LIHEAP applications
- **Monitors policy changes** — alerting when new energy assistance funds are appropriated

**MVP (6 weeks solo):** Eligibility screening + LIHEAP application assistance for 3 pilot states. Shut-off prevention letter generator.

## Stakeholders

- **48M eligible households** not using LIHEAP
- **1 in 3 US households** struggling with energy bills
- **LIHEAP administrators** (HHS/ACF, state grantees)
- **Community action agencies** (local LIHEAP implementers)
- **Utility companies** (disconnection prevention reduces bad debt)
- **Environmental justice organizations** (energy burden disproportionately affects communities of color)

## Data Sources

| Source | Description |
|---|---|
| [LIHEAP Program Data (HHS/ACF)](https://www.acf.hhs.gov/ocs/low-income-home-energy-assistance-program-liheap) | Eligibility guidelines, funding allocations, participation data |
| [DOE Weatherization Assistance Program](https://www.energy.gov/eere/wap/weatherization-assistance-program) | WAP eligibility and program data |
| [EIA Residential Energy Consumption Survey](https://www.eia.gov/consumption/residential/) | Energy burden, usage patterns by demographics |
| [LIHEAP Clearinghouse](https://liheapch.acf.hhs.gov/) | State-by-state program details and contacts |
| State utility commission websites | Utility discount programs, shut-off moratorium dates |

## Key Papers

- DOE (2023) — Energy burden in the United States
- HHS (2024) — LIHEAP Report to Congress
- Hernandez (2021) — Energy insecurity and health outcomes
- NEUAC (2024) — LIHEAP participation gap analysis
- Energy Justice Lab — Mapping energy burden by census tract

## Open Source Adjacencies

- Various state LIHEAP tools (none are open-source or reusable)
- [Benefits Data Trust](https://bdtrust.org/) — Benefits screening platforms (non-energy specific)
- [Code for America's GetCalFresh/GetYourBenefits](https://github.com/codeforamerica) — Benefits application tools (pattern to follow)
- [LIHEAP state toolkits](https://liheapch.acf.hhs.gov/tools.htm) — Static PDF toolkits, not software

## Success Criteria

- Complete an eligibility screening in under 3 minutes
- File a LIHEAP application in under 15 minutes (vs. 1+ hour currently)
- Achieve >50% conversion rate from screening → application submission (vs. 20% baseline)
- Generate a hardship/shut-off prevention letter accepted by utilities in testing
- Serve 1,000+ households in first 3 months of pilot
- Maintain 95%+ eligibility accuracy (no falsely denied applicants)

## Skills Needed

- **Full-stack web development** (React + Python/FastAPI)
- **State-specific program knowledge** (eligibility rules, forms, deadlines)
- **Document generation** (PDF form filling)
- **LLM integration** (natural language screening, hardship letter generation)
- **Accessibility** (low-literacy friendly, Spanish/English bilingual, mobile-first)
- **Data engineering** (multi-state rules engine, session state persistence)

## Risks

- **Program fragmentation:** 50+ states with different rules, forms, and deadlines. MVP must go deep (3 states) not wide.
- **Application uniqueness:** LIHEAP applications vary by state and sometimes by local agency. Generic form filling won't work everywhere.
- **Data recency:** Income guidelines and funding levels change annually. Automated update pipelines are essential.
- **Crisis sensitivity:** Users with shut-off notices need immediate help, not a dashboard. Must have "I need help NOW" pathways.
- **Screening accuracy:** False negatives (telling eligible people they don't qualify) are harmful. Conservative eligibility estimation is safer.
