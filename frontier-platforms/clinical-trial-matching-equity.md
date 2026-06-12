---
track: frontier-platforms
status: published
---

# Frontier 03 — Clinical Trial Matching & Patient Enrollment Equity Platform

> 85% of clinical trials fail enrollment targets. <5% of adult cancer patients participate. <10% of participants are racial minorities. FDA mandates Diversity Action Plans. No open-source patient-facing trial matching tool addresses equity.

## The Problem

$800K/day lost revenue per trial delay. Screen failure rates hit 51%. Black patients 3x underrepresented, Hispanic 18x — we don't know if drugs work on these populations. FDA Diversity Action Plans (DAPs) are now mandatory for Phase III. Existing tools (Carebox, myTomorrows, Medable) are expensive closed-source SaaS. An open-source platform with an equity analytics layer could solve a $40B+ market failure.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **ClinicalTrials.gov** | Keyword search only, free-text eligibility, no semantic matching |
| **Carebox** | Proprietary, expensive, institution-facing only |
| **myTomorrows** | Commercial expanded access, not equity-focused |
| **Medable** | Enterprise DCT platform, costs opaque |
| **TrialGPT (NIH)** | Research prototype, no patient interface, no equity layer |

## What to Build

- LLM-based eligibility criteria parser (fine-tuned on n2c2/LCT corpus)
- Semantic patient-trial matcher with per-criterion score breakdown
- Soft-match engine for protocol-justified broadening
- Equity analytics dashboard with FDA DAP report generation
- Provider dashboard with match recommendations

**MVP (3-4 months solo):** ClinicalTrials.gov ingestion → LLM eligibility parser → match scoring → equity dashboard → FDA DAP report generator

## Stakeholders

- 444M+ patients with conditions that have active trials
- 15,000+ pharma/biotech trial sponsors
- 5,000+ CROs coordinating enrollment
- 300M+ underrepresented patient populations
- FDA, EMA, PMDA regulators

## Data Sources

| Source | Description |
|--------|-------------|
| ClinicalTrials.gov | 444K+ trials, full protocol, free API |
| n2c2 2018 Cohort Selection | 288 patients, 13 criteria annotations |
| LCT Corpus | 1,000+ trials with granular eligibility data |
| TrialGPT datasets | 183 synthetic patients, 75K+ criterion annotations |

## Key Papers

- Jin et al. (2024) — "Matching patients to clinical trials with LLMs" — *Nature Communications*. 87.3% accuracy
- Miller et al. (2024) — "PRISM: Semantic Clinical Trial Matching" — *Nature Digital Medicine*. 35x cheaper than GPT-4
- Zhang et al. (2020) — "DeepEnroll: Deep Embedding for Patient-Trial Matching" — *arXiv*. 12.4% F1 improvement
- Stubbs et al. (2019) — "Cohort selection: n2c2 2018 shared task" — *JAMIA*. Best system 0.91 F1

## Open Source Adjacencies

- [Trialibre](https://github.com/matthewhmaxwell/trialibre) — MIT, criterion-level matching
- [TrialGPT](https://github.com/ncbi-nlp/TrialGPT) — NIH/NLM, end-to-end retrieval + matching
- [EliIE](https://github.com/Tian312/EliIE) — Eligibility criteria IE into OMOP CDM

## Skills Needed

- LLM fine-tuning (Hugging Face)
- FHIR/EHR data models
- React + FastAPI
- Health equity analytics
- ClinicalTrials.gov API

## Risks

- ClinicalTrials.gov data quality — many trials outdated
- EHR integration — FHIR APIs inconsistently implemented
- Liability — wrong match could deny life-saving treatment
- Competitors well-funded (Carebox $60M+)
