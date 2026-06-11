---
track: us-civic-tech
status: published
---

# HousingKey — Low-Income Housing Program Navigator

> 20 million+ eligible households receive no housing assistance. The system that's supposed to help is a fragmented maze of Section 8, public housing, LIHTC, vouchers, and state programs. Unlock access.

## The Problem

Housing assistance in the United States is not a single program — it's a fragmented, overlapping, and bewildering patchwork. **Section 8 vouchers, public housing, project-based vouchers, LIHTC (Low-Income Housing Tax Credit) properties, state trust funds, local rental assistance, and emergency housing vouchers** — each with different eligibility rules, application processes, waitlists, and timelines.

**12 million+ households** receive some form of federal housing assistance — but **20 million+ more** are eligible and unserved. Meanwhile, **500,000+ people** experience homelessness on any given night. The waitlist for Section 8 vouchers in major cities can be **5–10 years** or more, and most are permanently closed to new applicants.

The burden of navigating this system falls on the most vulnerable: low-income families, seniors on fixed incomes, people with disabilities, and veterans. Understanding which programs you qualify for, how to apply, where waitlists are open, and what preferences you might have (veteran, elderly, disability, homeless) is a full-time job — one that most people in crisis simply cannot do.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| HUD website | Raw program information; no personalization or navigation |
| Local PHA offices | Understaffed; long phone waits; limited hours; no online tools |
| 211 / social services | General referral; no application assistance or follow-up |
| Housing counseling agencies | In-person only; limited capacity; 4–6 week waits |
| Online rental platforms (Zillow, Apartments.com) | Market-rate only; no subsidy/section 8 listings |
| **No comprehensive navigator exists** | No tool connects eligibility → application → waitlist → housing |

## What to Build

A housing assistance navigator that:

- **Runs an eligibility engine** — income + household size + location + characteristics → all programs user qualifies for (% AMI-based)
- **Tracks waitlists** — which are open, estimated wait times, how to apply, when to check back
- **Automates applications** — one intake form → pre-fills applications for as many programs as possible
- **Screens for preferences** — veteran, elderly, disability, homeless, domestic violence — factors that increase priority
- **Provides hearing preparation** — for Section 8 terminations, eviction defense, and fair housing complaints
- **Guides lottery-based applications** — for LIHTC properties and housing lotteries
- **Generates housing advocacy briefs** — for caseworkers and advocates

**MVP (10–12 weeks solo):** Eligibility engine + waitlist tracking for Section 8 and public housing. Single-user web app covering 1–2 major metro areas.

## Stakeholders

- **12M+ households** currently receiving housing assistance
- **20M+ eligible but unserved households** (worst-case housing needs)
- **500K+ homeless individuals** on any given night
- **Public Housing Authorities (PHAs)** nationwide
- **Housing advocates and legal aid organizations**
- **Continuums of Care (CoCs)** — local homeless service coordinators

## Data Sources

| Source | Description |
|---|---|
| [HUD Picture of Subsidized Households](https://www.huduser.gov/portal/datasets/picture/yearlydata.html) | Demographics of households in assisted housing |
| [HUD Fair Market Rents](https://www.huduser.gov/portal/datasets/fmr.html) | Income limits and rent standards by metro area |
| [LIHTC Database](https://www.huduser.gov/portal/datasets/lihtc.html) | All tax-credit properties with unit counts and rent levels |
| [National Housing Preservation Database](https://preservationdatabase.org/) | At-risk affordable housing properties |
| [Census PUMS / ACS](https://www.census.gov/programs-surveys/acs/) | Household income, composition, and housing cost burden |

## Key Papers

- Desmond (2016) — Evicted: Poverty and Profit in the American City
- JCHS (2024) — State of the Nation's Housing
- HUD PD&R — Worst Case Housing Needs (biennial report)
- Urban Institute — Housing assistance and the eligibility gap
- Center on Budget and Policy Priorities — Section 8 and public housing fact sheets

## Open Source Adjacencies

- [Housing Insights](https://github.com/codefordc/housing-insights) — DC-area housing data explorer
- [National Housing Preservation Database](https://github.com/preservationdatabase/nhpd-api) — Preservation database API
- [HUD Data API](https://www.huduser.gov/portal/dataset/hud-data-api.html) — Multiple HUD datasets via API
- [PolicyMap](https://www.policymap.com/) — Commercial; open-data patterns to follow
- [District Dirty Data](https://github.com/codefordc/dirty-data) — Housing data cleaning tools

## Success Criteria

- Determine eligibility for 5+ federal housing programs from a 3-minute intake
- Track 100% of open waitlists in 2 pilot metro areas
- Complete a Section 8 application pre-fill in under 10 minutes
- Generate a waitlist status report with estimated wait times
- Reduce the average time from "I need help" → "I have applied" from weeks to <30 minutes

## Skills Needed

- **Full-stack development** (React + Python/Node.js)
- **Eligibility rules engine** (% AMI calculation, household composition logic)
- **LLM integration** (natural language intake, plain-language program explanations)
- **Document generation** (PDF form filling for housing applications)
- **Data engineering** (multi-source HUD data integration, waitlist tracking)
- **Housing policy knowledge** (Section 8, public housing, LIHTC, voucher types)

## Risks

- **Waitlist volatility:** PHAs open and close waitlists unpredictably. Must have real-time or near-real-time monitoring.
- **Preference complexity:** Veteran, disabled, elderly, homeless — preferences vary by PHA and program. Rules engine must be detailed.
- **Data freshness:** HUD data lags by 1–2 years. Need supplemental real-time sources.
- **Client vulnerability:** Homelessness and housing insecurity are traumatic. Trauma-informed design is essential.
- **Scope creep:** Housing programs are deeply varied. MVP must resist the temptation to cover everything — pick 1–2 metro areas and go deep.
