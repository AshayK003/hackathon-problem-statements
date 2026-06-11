---
track: global-south-impact
status: published
---

# Maternal Health Risk Stratification for Low-Resource Settings

> Public Health | Maternal Health — 6–8 month build

## The Problem

Every day, approximately 712 women die from preventable causes related to pregnancy and childbirth — 94% of these deaths occur in Low- and Middle-Income Countries (LMICs). The vast majority are preventable with timely identification of risk factors and appropriate referral. Existing risk scores are paper-based, static, and have only been validated in high-resource settings. Community health workers (CHWs) in rural clinics lack any AI-assisted decision support to stratify patients, prioritize home visits, or trigger referrals. A lightweight, offline-first machine learning system running on $30 Android phones could dramatically improve early detection of high-risk pregnancies and reduce maternal mortality in the communities that need it most.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| WHO Maternity Risk Score (paper-based) | Static checklist, validated only in hospital settings, no personalization |
| Countdown to 2030 dashboards | National-level aggregates, no individual risk stratification |
| High-resource EHR risk models (e.g., MFMU, APEX) | Require rich longitudinal data, labs, and continuous internet — unavailable in LMICs |
| Manual CHW triage | Highly variable accuracy, no decision support, no learning from outcomes |

## What to Build

- An ensemble ML pipeline combining nutrition status, infection history, vital signs, and prior pregnancy outcomes into a real-time risk score
- A TensorFlow Lite model (offline-capable, <10 MB) deployable on $30–50 Android phones with no internet dependency
- A simple mobile-first interface for community health workers: scan patient ID, enter basic vitals, receive risk category (low/medium/high) + referral action
- Transfer learning from high-resource EHR datasets (e.g., Brazilian DATASUS, US MFMU) adapted to LMIC feature sets via domain-adversarial training
- Privacy-preserving federated learning pipeline for continuous model improvement across clinics without centralizing patient data
- Dashboard for district health officers showing risk distribution, referral completion rates, and population-level trends

## Stakeholders

- **287,000+ maternal deaths/year** in LMICs that could be prevented with better risk stratification
- **7+ million community health workers** worldwide who serve as the frontline of maternal care
- **Ministries of Health** in LMICs seeking to reduce maternal mortality ratios (MMR)
- **WHO, UNICEF, UNFPA** — global bodies funding maternal health programs
- **Pregnant women in rural and underserved communities** who currently receive no systematic risk assessment

## Data Sources

- **WHO Multi-Country Survey on Maternal and Newborn Health** — 314,000 women across 29 countries, gold standard for LMIC maternal outcomes
- **Demographic and Health Surveys (DHS) Program** — 90+ countries, representative household data on maternal health, nutrition, and socioeconomic factors
- **Brazilian DATASUS (SINASC/SIM)** — 80+ million birth records with rich clinical detail, publicly available
- **Kaggle Maternal Health Risk Dataset** — curated vital signs + risk labels for rapid prototyping
- **Maternal Mortality Estimation Inter-Agency Group (MMEIG)** — country-level mortality trends and cause-of-death distributions

## Key Papers

- Kassahun, A. et al. (2024) — "Machine learning for maternal health risk prediction in low-resource settings" — systematic review of ML approaches for LMIC contexts
- Rocha, T. et al. (2021) — "Using DATASUS for maternal health surveillance: opportunities and challenges" — demonstrates large-scale Brazilian data utility
- Scientific Reports (2025) — "Ensemble methods outperform single classifiers for pregnancy complication prediction in South Asian cohorts"
- WashU / ICPI (2025) — "Transfer learning from high-resource EHR to LMIC community health worker data for preterm birth prediction"

## Open Source Adjacencies

- **Hikma Health** — open-source mobile health platform designed for refugee and low-resource settings
- **DHIS2** — world's largest open-source health information management system, used by 80+ countries
- **OpenMRS** — open-source medical record system for LMICs, extensive maternal health module
- **TensorFlow Lite / TFLite Model Maker** — framework for on-device ML inference
- **FATE (Federated AI Technology Enabler)** — open-source framework for privacy-preserving federated learning

## Success Criteria

- [ ] Model achieves AUC ≥ 0.85 on held-out WHO Multi-Country Survey data
- [ ] TFLite model runs in < 2 seconds inference on a $30 Android phone
- [ ] AppUI tested with 20+ CHWs in a simulated low-resource clinic workflow
- [ ] Risk score outperforms paper-based WHO score by ≥ 15% in precision-recall on a held-out LMIC cohort
- [ ] Federated learning pipeline converges within 5% of centralized model performance
- [ ] Offline mode fully functional: all core features work with zero internet connectivity

## Skills Needed

- 2× Machine Learning Engineers (tabular data, ensemble methods, transfer learning, TFLite export)
- 1× Mobile Developer (Android, offline-first architecture, low-bandwidth sync)
- 1× Public Health / Maternal Health Domain Expert (LMIC experience, CHW workflow knowledge)

## Risks

| Risk | Mitigation |
|---|---|
| LMIC clinical data is sparse and noisy | Use transfer learning from high-resource data; build in uncertainty estimation |
| CHWs have low digital literacy | Co-design UI with CHW focus groups; use icon-based navigation, local language voice prompts |
| Regulatory barriers to deploying ML in clinical decision-making | Position as "advisory" not "diagnostic"; engage Ministry of Health early for ethical clearance |
| Model drift over time as population health changes | Continuous evaluation pipeline; federated learning with automatic drift detection triggers |
| Phone cost still prohibitive for some CHWs | Target $30 devices; explore SMS-based fallback for basic risk reporting |
