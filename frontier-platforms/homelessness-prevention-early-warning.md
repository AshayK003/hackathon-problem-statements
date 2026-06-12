---
track: frontier-platforms
status: published
---

# Frontier 04 — Homelessness Prevention & Housing Stability Early Warning System

> 653K homeless on a single US night. 3.6M evictions filed annually. Allegheny County proved ML identifies 28% more at-risk individuals than reactive triage. No generalizable open-source platform exists for the 3,000+ US counties that need this.

## The Problem

$200K annual cost per chronically homeless person (ED visits, jail, shelter) vs. $25K for prevention. 1 in 4 tenants face eviction in their lifetime. Every county builds its own bespoke ML system at enormous cost. An open-source platform that ingests court eviction filings, 911/EMS calls, ED visits, and benefits data — trains a fair ML model, and integrates with case management — could reduce homelessness by 30% through targeted prevention.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **Allegheny County DHS** | Custom-built, not generalizable, needs data warehouse |
| **LA County HMS** | Custom-built, proprietary |
| **NYC Homebase** | Reactive (walk-in), not predictive |
| **NCALL** | Single-purpose eviction filing only |
| **211 systems** | Reactive — person must call for help |

## What to Build

- Data ingestion pipeline for court filings, 911/EMS, ED visits, SNAP/TANF, school homelessness data
- Risk prediction model (XGBoost) trained on historical outcomes — proven 28% improvement
- Fairness-constrained optimization ensuring equal FPR/FNR across racial groups
- Prevention resource matcher — rental assistance, legal aid, mediation
- Case manager dashboard with prioritized risk list and referral automation

**MVP (4-5 months solo):** Court records ingestion → risk model (trained on Eviction Lab + ACS) → fairness audit → dashboard → pilot with 1-2 counties

## Stakeholders

- 653K+ unhoused on any night (3M+ annually)
- 3.6M+ tenants facing eviction annually
- 3,000+ US counties with homeless systems
- 10,000+ homeless service providers
- HUD, VA, HHS

## Data Sources

| Source | Description |
|--------|-------------|
| HUD PIT Counts | Annual homeless counts (2007-2023) |
| Eviction Lab (Princeton) | 82M eviction records (2000-2018), public |
| US Census ACS | Housing cost burden, poverty, demographics |
| HUD AHAR | Annual Homeless Assessment Report |

## Key Papers

- Vajiac et al. (2024) — "Preventing Eviction-Caused Homelessness through ML-Informed Rental Assistance" — *AAAI 2024*. 28% improvement, fair across race/gender
- Allegheny County CMU DSSG (2023) — "Data-Driven Models for Eviction Prevention"
- Culhane et al. (2021) — "Using Integrated Data Systems to Address Homelessness" — *ANNALS AAPSS*
- Byrne et al. (2019) — "Predicting Homelessness Among Veterans" — *HSR*

## Open Source Adjacencies

- [eviction-risk-prediction](https://github.com/cruzlawrencemayes/eviction-risk-prediction) — ML analysis project
- **No generalizable open-source homelessness early warning platform exists**

## Skills Needed

- ML (XGBoost, LightGBM, fairness constraints)
- Data engineering (court data, HMIS integration)
- React + FastAPI
- Government IT integration
- Privacy engineering (PII-heavy data)

## Risks

- Eviction/homelessness data is extremely sensitive; community governance required
- Predictive models targeting poor populations risk reinforcing discrimination
- County data access requires MOUs and legal agreements
- False positives waste scarce prevention resources
- Each county has different IT systems, data quality, politics
