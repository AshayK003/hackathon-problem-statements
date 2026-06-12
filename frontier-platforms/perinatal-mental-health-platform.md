---
track: frontier-platforms
status: published
---

# Frontier 09 — Perinatal (Maternal) Mental Health Screening & Navigation Platform

> 1 in 5 birthing individuals affected by perinatal mental health disorders — leading cause of maternal death in US, UK, Australia. 75% go undetected. No open-source platform integrates screening, risk prediction, and navigation.

## The Problem

4M+ annual US births; 800K+ affected. Maternal suicide is the leading cause of maternal death. US maternal mortality (32.9/100K) is highest in developed world; Black women affected 2-3x more. Universal screening is recommended by ACOG, AAP, USPSTF — but <50% of providers screen consistently. Existing tools are paper-based, commercial (nurtur, Maven, Ovia), or limited to research. An open-source platform any OB practice, midwifery group, or health department could deploy would save mothers' lives.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **Paper screenings (EPDS, PHQ-9)** | Not scored/tracked consistently; results not shared |
| **nurtur (UK)** | AI-powered but commercial; UK-only focus |
| **Maven** | Telehealth platform; not MH-focused |
| **Ovia** | Fertility tracking; limited MH component |
| **Epic EPDS module** | Embedded in expensive EHR; not standalone |

## What to Build

- Digital screening engine (EPDS, PHQ-9, GAD-7, PSAS) with automatic scoring + longitudinal tracking
- Risk prediction model (LightGBM) — screening + risk factors (prior depression, trauma, financial stress, social support)
- Automated triage & referral — self-guided → support groups → therapy → psychiatrist → crisis (988, PSI helpline)
- Equity module — culturally adapted screening, preferred language, race-stratified outcomes tracking
- Provider decision support — "patient's EPDS up 5 points — consider escalation"

**MVP (2-3 months solo):** Digital EPDS/PHQ-9 → automatic scoring + tracking → risk model → triage → provider dashboard

## Stakeholders

- 4M+ annual US births (800K+ affected annually)
- 80,000+ OB/GYN providers
- 25,000+ midwives, doulas, NPs
- 2,000+ birthing hospitals
- Health departments serving Medicaid mothers

## Data Sources

| Source | Description |
|--------|-------------|
| PRAMS (CDC) | State-level maternal health data |
| CDC WONDER | Maternal mortality data |
| NSDUH (SAMHSA) | Maternal MH indicators |
| EPDS validation datasets | Multiple public research datasets |
| PHRASES | Policy Center for Maternal Mental Health |

## Key Papers

- Kendig et al. (2017) — "Consensus Bundle on Maternal Mental Health" — *JOGNN*. ACOG-endorsed pathway
- Earls et al. (2019) — "Perinatal Depression into Pediatric Practice" — *Pediatrics*. AAP policy
- O'Connor et al. (2023) — "Screening for Depression and Suicide Risk" — *JAMA*. USPSTF recommendation
- Vogel et al. (2023) — "Maternal suicide: leading cause of maternal death" — *BMJ Global Health*
- Wisner et al. (2013) — "Onset timing, self-harm in postpartum women" — *JAMA Psychiatry*

## Open Source Adjacencies

- [StillMind](https://github.com/StillMind) — Mental health triage (adapt for perinatal)
- [AI-Mental-Health-Triage](https://github.com/dszohib) — NLP + risk prediction
- [OpenEMR](https://github.com/openemr/openemr) — Could host perinatal screening module
- **No dedicated open-source perinatal MH platform exists**

## Skills Needed

- Clinical screening instruments (EPDS, PHQ-9, GAD-7)
- ML (LightGBM, clinical risk modeling)
- React + FastAPI
- Health equity analytics
- HIPAA compliance engineering

## Risks

- Screening without treatment pathways is harmful — referral infrastructure essential
- EPDS validated primarily in English/white — culturally adapted screening needed
- Black maternal mortality 2-3x higher; platform must actively address disparities
- Screening may require FDA clearance as medical device
- Competition: nurtur ($6M), Maven ($90M+)
