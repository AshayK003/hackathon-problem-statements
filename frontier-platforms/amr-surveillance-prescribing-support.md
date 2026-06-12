---
track: frontier-platforms
status: published
---

# Frontier 05 — Antimicrobial Resistance Surveillance & Prescribing Decision Support

> AMR will kill 10M people/year by 2050 — surpassing cancer. WHONET (WHO's surveillance tool) is a Windows-only desktop app from the 1990s. No open-source web platform combines surveillance, antibiograms, resistance prediction, and prescribing decision support.

## The Problem

1.27M annual deaths already attributable to AMR. 70% of antibiotics globally used in agriculture. Every hospital has microbiology lab data — siloed in paper logs, WHONET databases, or proprietary instrument software. Clinicians prescribe blind without local resistance patterns. WHO GLASS reports aggregate months late. An open-source platform that ingests lab data, computes local antibiograms, predicts resistance probabilities, and recommends appropriate antibiotics would transform global AMR management.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **WHONET (WHO/BWH)** | Windows-only, no API, no ML, no web, no clinical CDS |
| **CDC NARMS** | US-only retrospective reports, not real-time |
| **WHO GLASS** | Aggregate reporting, not for clinical use |
| **Pfizer ATLAS** | Pharma-sponsored, selective coverage, not open |
| **bioMerieux LUMED** | Commercial, requires bioMerieux instruments |

## What to Build

- Microbiology lab data ingestion (HL7/FHIR or CSV → canonical format)
- CLSI M39-A2 compliant local antibiogram generator with trend analysis
- Resistance prediction model (LightGBM) — organism-drug resistance probability
- Prescribing decision support — patient factors + antibiogram + predictions → ranked antibiotics
- One Health integration — veterinary + wastewater AMR data
- Outbreak detection via statistical process control on resistance rates

**MVP (4-6 months solo):** Lab data model + CSV import → antibiogram generator → resistance prediction → prescribing CDS → FHIR integration

## Stakeholders

- 7.7B people — everyone needs effective antibiotics
- 10M+ clinicians prescribing antibiotics daily
- 50,000+ hospitals with microbiology labs
- 194 WHO member states with AMR commitments
- Livestock farmers using antibiotics

## Data Sources

| Source | Description |
|--------|-------------|
| WHO GLASS | Standardized surveillance, 44+ countries |
| CDC NARMS | US retail meat, animal, human isolates (1996-present) |
| Pfizer ATLAS | Global, 60+ countries (2004-present) |
| CARD | Comprehensive Antibiotic Resistance Database |
| BV-BRC (PATRIC) | Bacterial genomics + AMR metadata |

## Key Papers

- ML Prediction of Antibiotic Resistance from Structure (2025) — *Nature Scientific Reports*. >85% AUC
- AI in Drug Resistance Management (2025) — *PMC*. Comprehensive review
- Forecasting AMR Trends using WHO GLASS (2026) — *arXiv*. First ML study on GLASS
- Jin et al. (2022) — "ML for AMR Prediction: Current State and Future Directions" — *Clinical Microbiology Reviews*

## Open Source Adjacencies

- [WHONET](https://whonet.org/) — Windows desktop AMR database
- [CARD](https://github.com/arpcard) — AMR gene detection (McMaster)
- [AMR++](https://github.com/AMRPlusplus) — Bioinformatics AMR pipeline
- **No open-source web-based surveillance + CDS platform exists**

## Skills Needed

- Clinical microbiology data standards (CLSI, HL7/FHIR)
- Python ML (LightGBM)
- Web development (React + Python/FastAPI)
- Global health data standards (WHO GLASS)

## Risks

- Lab data formats vary wildly across 130+ countries
- WHONET has 30+ years of penetration; switching costs are real
- Many hospitals won't send lab data to the cloud
- Medical CDS may require FDA/CE clearance
- bioMerieux bundles surveillance with lab instruments
