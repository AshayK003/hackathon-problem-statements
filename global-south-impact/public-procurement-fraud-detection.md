---
track: global-south-impact
status: published
---

# Public Procurement Fraud Detection & Transparency Platform

> Governance | Anti-Corruption — 5–7 month build

## The Problem

Governments worldwide spend 10–20% of GDP on public procurement — over $13 trillion annually. An estimated 10–30% of this spending is lost to fraud, corruption, and bid-rigging each year. The Open Contracting Data Standard (OCDS) has enabled 50+ countries to publish procurement data in a structured format, yet this data sits largely unused by oversight bodies, civil society, and the public. Existing fraud detection relies on slow, manual audits that catch only a tiny fraction of violations. An AI-powered platform that ingests OCDS data, applies graph neural networks to detect bid-rigging rings, uses LLMs to extract red flags from tender documents, and surfaces anomalies in real-time could dramatically improve public spending transparency and save billions of dollars for essential public services.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| Manual supreme audit institution reviews | Catch <1% of fraudulent contracts; each audit takes months |
| Rule-based procurement monitoring (e.g., e-procurement flags) | High false-positive rates; miss novel or adaptive fraud patterns |
| Single-country custom platforms | Not transferable; require expensive re-engineering per jurisdiction |
| Traditional statistical tests (Benford's Law, price variance) | Oversimplified; ignore network/graph structure of bidding rings |
| Journalistic investigations (e.g., OCCRP, ICIJ) | Deep but extremely narrow in scope; reactive, not proactive |

## What to Build

- Graph Neural Network pipeline that ingests OCDS-structured bid data and detects collusive bidding patterns (bid rotation, complementary bidding, market allocation, subcontracting loops)
- LLM-based red flag extraction from unstructured tender documents, contract amendments, and beneficial ownership disclosures
- Anomaly detection on price, winner concentration, procurement method, and timeline deviations using unsupervised and weakly-supervised methods
- Interactive dashboard for Supreme Audit Institutions (SAIs), journalists, and civil society showing risk-scored contracts, entity networks, and drill-down evidence packages
- Open API allowing third-party developers and country-level portals to consume fraud risk scores
- Cross-country transfer learning so model performance improves as more jurisdictions adopt OCDS

## Stakeholders

- **188 countries** pursuing public procurement reforms (World Bank procurement framework)
- **194 Supreme Audit Institutions (INTOSAI members)** responsible for auditing government spending
- **Civil society organizations** (Transparency International, Global Integrity, Open Contracting Partnership)
- **Citizens and taxpayers** in LMICs where procurement fraud directly reduces funds for schools, clinics, and infrastructure
- **Procurement regulators and anti-corruption commissions** (e.g., Kenyan PPRA, Nigerian BPP, Philippine GPPB)

## Data Sources

- **BidCorpus (HuggingFace)** — curated dataset of structured procurement records with fraud labels for model development
- **OCDS Global Data** — 50+ countries publishing standardized contract data via the Open Contracting Data Standard; 10M+ contracts available
- **US FPDS-NG (Federal Procurement Data System)** — 20+ years of detailed US federal contract data
- **EU TED (Tenders Electronic Daily)** — 700K+ procurement notices/year from EU member states
- **World Benchmarking Alliance — Open Contracting data** — country-level adoption scores and data quality assessments
- **Ukraine ProZorro** — world's most transparent procurement system, with open data since 2016 and known fraud cases

## Key Papers

- Schneider dos Santos, C. et al. (2025) — "Graph neural networks for procurement fraud detection: a comparative study on cross-country OCDS data"
- Utrecht University (2026) — "LLM-assisted red flag detection in public procurement: extracting risk signals from unstructured tender text"
- Lima, M. et al. (2025) — "Benchmarking anomaly detection methods on BidCorpus: from statistical tests to deep learning"

## Open Source Adjacencies

- **OCDS Standard** (Open Contracting Partnership) — data schema and tools for publishing structured procurement data
- **NetworkX** — Python library for graph/network analysis, foundational for GNN preprocessing
- **PyTorch Geometric** — deep learning framework for graph neural networks
- **HuggingFace Transformers** — LLM backbone for document-level fraud signal extraction
- **OpenProcurement / ProZorro** — open-source e-procurement system used by Ukraine and adapted in other countries

## Success Criteria

- [ ] GNN model achieves AUC ≥ 0.90 on BidCorpus held-out test set for bid-rigging detection
- [ ] LLM document screening reduces manual document review volume by ≥ 80% while maintaining ≥ 90% fraud recall
- [ ] Platform ingests and scores procurement data from ≥ 5 OCDS-publishing countries in real-time
- [ ] Dashboard playable by non-technical auditors (validated via user testing with ≥ 5 audit professionals)
- [ ] Cross-country transfer shows ≤ 5% performance drop when model trained on 3 countries is applied to a 4th unseen country
- [ ] Open API documented and published with ≥ 3 external prototype integrations shown

## Skills Needed

- 2× Machine Learning Engineers (graph neural networks, NLP, anomaly detection, PyTorch)
- 1× Full-Stack Developer (data pipeline, dashboard, API, visualization)
- 1× Anti-Corruption / Governance Domain Expert (public procurement, OCDS, audit workflows)

## Risks

| Risk | Mitigation |
|---|---|
| Fraud labels are rare and hard to obtain in training data | Use weakly-supervised and self-supervised learning; generate semi-synthetic collusion rings for augmentation |
| OCDS data quality varies wildly across countries | Build data quality scoring layer; allow graceful degradation per country source |
| Political pushback from governments exposed by the system | Platform is designed for SAIs and civil society, not unilateral publication; emphasize evidence-packaging for official investigations |
| Language diversity in tender documents | Start with English/Spanish/French; use multilingual LLMs (Gemma, Llama, GPT) with translation fallback |
| Class imbalance — fraudulent contracts are <1% of all contracts | Use anomaly detection framing; evaluate on precision at low recall thresholds (e.g., P@100, P@1000) |
