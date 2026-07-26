---
track: frontier-platforms
status: published
---

# Frontier 02 — Youth Mental Health Crisis Triage & Navigation System

> Suicide is the 2nd leading cause of death for ages 10-24. 20% of US youth (12-17) had a major depressive episode in 2024. School counselors face 1:500 ratios. No open-source system integrates screening with NLP writing analysis for early risk detection.

## The Problem

49,000+ US suicide deaths/year — 1 every 11 minutes. 50% of lifetime mental illness begins by age 14. Schools use paper screenings (PHQ-A, GAD-7), overwhelmed counselors, and fragmented crisis line referrals. An integrated system that screens digitally, analyzes student writing for linguistic distress markers, stratifies risk via ML, and navigates to appropriate care (self-guided → school counselor → 988 crisis line → emergency services) could save lives — but nothing like this exists in open source.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **Paper screenings (PHQ-A, GAD-7)** | Manual scoring, no longitudinal tracking, no NLP |
| **Crisis Text Line** | Reactive only — person must reach out |
| **988 Lifeline** | Overwhelmed call centers, no pre-crisis pipeline |
| **CHADIS** | Pediatric screening only, no youth triage, no school integration |
| **NeuroFlow** | Expensive enterprise B2B, no standalone youth module |

## What to Build

- Digital screening engine (PHQ-A, GAD-7, C-SSRS) with automatic scoring + longitudinal trends
- NLP distress detector using fine-tuned DistilBERT on opt-in student writing
- Risk stratification model (LightGBM) combining screening + NLP + behavioral data
- Navigation recommender mapping risk tier → appropriate intervention pathway
- Counselor dashboard with real-time risk alerts

**MVP (3-4 months solo):** Digital screening → NLP distress detector → risk stratification model → counselor dashboard. Pilot with 1-2 school districts.

## Stakeholders

- 50M+ US K-12 students (1 in 5 with diagnosable condition)
- 4.5M school counselors, social workers, psychologists
- 100M+ parents
- 13,000+ US school districts

## Data Sources

| Source | Description |
|--------|-------------|
| CDC YRBS | Biannual youth risk behavior survey |
| SAMHSA NSDUH | Youth 12-17 substance use and mental health |
| NIMH ABCD Study | 12K youth, longitudinal brain/cognitive development |
| Healthy Minds Study | College student mental health (public) |

## Key Papers

- Su et al. (2020) — "ML for Suicide Risk Prediction in Children" — *Translational Psychiatry*. AUC 0.81-0.86
- Penfold et al. (2021) — "Predicting Suicide Attempts Among Adolescents" — *J Affective Disorders*. AUC 0.80-0.86
- Baba & Bunji (2023) — "Prediction of MH Using Annual Student Survey" — *JMIR Mental Health*. LightGBM AUC 0.838
- Xu et al. (2023) — "Mental-LLM: LLMs for Mental Health Prediction" — *arXiv*

## Open Source Adjacencies

- [StillMind](https://github.com/StillMind) — Rule-based triage for student counseling
- [AI-Mental-Health-Triage](https://github.com/dszohib) — NLP + risk prediction
- [Aware (29k)](https://github.com/29ki/29k) — AGPL MH awareness app

## Skills Needed

- NLP (transformers, DistilBERT)
- ML (XGBoost/LightGBM)
- FERPA-compliance engineering
- React + FastAPI
- Clinical screening instruments (PHQ-A, GAD-7)

## Risks

- False positives cause real harm — conservative thresholds required
- FERPA/HIPAA complexity — legal risk if data shared improperly
- NLP may underperform on non-English, neurodivergent students
- School district sales cycles (6-12 months)
- Liability if flagged student dies by suicide
