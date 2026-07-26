---
track: frontier-platforms
status: published
---

# Frontier 06 — Dementia / Alzheimer's Caregiver Decision Support Platform

> 55M people have dementia (139M by 2050). $1T+ annual cost. 11M+ unpaid US caregivers get zero systematic decision support. No open-source platform combines behavior prediction, evidence-based recommendations, and care coordination.

## The Problem

Family caregivers face agonizing decisions daily: when to take away car keys, move to memory care, manage sundowning, choose medications. 40-70% have clinically significant stress; 30% have major depression. Existing tools are basic medication reminders, information portals, or proprietary AI requiring clinical teams. No evidence-based, open-source decision support exists for the 55M families navigating dementia.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **Alzheimer's Association website** | Information portal only, no personalization |
| **Simon.health** | Education videos + companion; no AI decision support |
| **Rippl/Kinto** | Requires clinical team involvement; acquired/commercial |
| **mySeniorCareHub** | Basic check-in (reminders, GPS); no intelligence |
| **Carely** | Family coordination only; no clinical CDS |

## What to Build

- Passive behavior pattern detection (smart home sensors, wearables) for agitation/wandering precursors
- Risk prediction: patient stage + comorbidities + meds + environment → fall, institutionalization, burnout, hospitalization risk
- Evidence-based RAG recommendation engine over dementia care literature (BEHAVE-AD, CMS, Alzheimer's Association)
- Care coordination dashboard: shared calendar, medication management, provider portal
- Disease trajectory visualization with proactive planning prompts

**MVP (3-4 months solo):** Needs assessment tool → care coordination dashboard → RAG recommendation engine → risk prediction

## Stakeholders

- 55M+ people with dementia (139M by 2050)
- 11M+ unpaid US caregivers (40M+ globally)
- 2M+ paid caregivers in nursing homes
- 100K+ geriatricians and neurologists (massive shortage)

## Data Sources

| Source | Description |
|--------|-------------|
| ADNI | 5,000+ participants, cognition, biomarkers (DUC required) |
| NACC | 40+ Alzheimer's centers longitudinal data (DUC required) |
| UK Biobank | 500K participants, cognitive assessments |
| NHATS/NSOC | Function + caregiving + caregiver burden (public) |
| HCAP | Dementia assessment in 45K+ HRS households |

## Key Papers

- Assistive Intelligence Framework (2025) — "AI-Powered Technologies Across the Dementia Continuum" — *MDPI*
- Saha et al. (2026) — "Mapping Caregiver Needs to AI Chatbot Design" — *ACM Trans Computing for Healthcare*
- Sun et al. (2025) — "Interactive AI Technology for Dementia Caregivers" — *J Technology in Human Services*
- UCSF Care Ecosystem — Validated remote collaborative dementia care model
- Wimo et al. (2023) — "The worldwide costs of dementia 2023" — *J Alzheimer's Disease*

## Open Source Adjacencies

- RecallMe — Flutter on-device dementia companion
- [Beacon](https://github.com/Beacon-Health) — Assistive tech for aging
- **No comprehensive caregiver decision-support platform is open-source**

## Skills Needed

- RAG / LLM integration for evidence retrieval
- Time series anomaly detection (behavior patterns)
- React + FastAPI
- Clinical knowledge curation (dementia care)

## Risks

- Dementia care evidence has fewer RCTs than other fields
- Caregivers are stressed and time-poor — must be dead simple
- Medical recommendations without clinician oversight = legal risk
- Monitoring behavior raises privacy/autonomy concerns
- Rippl ($65M) + Kinto ($6M NIH) have commercial momentum
