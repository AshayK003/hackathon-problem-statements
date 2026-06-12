---
track: frontier-platforms
status: published
---

# Frontier 10 — SMB Cybersecurity Compliance Automation Platform

> 43% of cyberattacks target small businesses. 60% go out of business within 6 months of a breach. 33M US SMBs need affordable compliance — but existing open-source tools focus only on tech startups and SOC 2/ISO 27001.

## The Problem

Regulations exploding: CCPA, GDPR, HIPAA, PCI-DSS, CMMC, 15+ state privacy laws. Traditional tools (Vanta, Drata, Secureframe) cost $10K-$50K+/year. Open-source tools (Comp AI, Probo) serve VC-funded tech startups, not Main Street (retail, construction, professional services). No platform provides a compliance navigator that maps an SMB's specific obligations and automates evidence collection from their tech stack.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **Vanta** | $10K+/year, SOC 2 only, startup focused |
| **Drata** | $15K+/year, startup focused |
| **Comp AI** | Open-source, SOC 2/ISO 27001 only, startup focused |
| **Probo** | Open-source GRC, engineering team focused |
| **DIY spreadsheets** | Can't produce evidence; unreliable |

## What to Build

- Regulatory obligation mapper — business type + size + location + revenue → applicable regulations
- Control framework generator — tailored from applicable regs (no over/under-compliance)
- Evidence collection agents — connectors for Google Workspace, QuickBooks, Square, Shopify, AWS
- Risk-based prioritizer — highest-risk controls first given SMB budget constraints
- Audit report automation — regulator-ready documentation
- AI policy writer — context-specific security policies for non-technical owners

**MVP (2-3 months solo):** Regulatory KB (20+ regulations) → compliance questionnaire → control framework → basic connectors → audit reports

## Stakeholders

- 33M US small businesses (99.9% of all businesses)
- 62M+ US SMB employees
- 300K+ defense contractors affected by CMMC
- Every healthcare practice (HIPAA), every business with CA customers (CCPA)
- Cyber insurance industry ($30B+ market)

## Data Sources

| Source | Description |
|--------|-------------|
| CVE / NIST NVD | Common vulnerabilities |
| CISA KEV | Known Exploited Vulnerabilities |
| NIST CSF | Cybersecurity Framework (free) |
| NIST SP 800-53 | Control catalog |
| CMMC Model (DoD) | Cybersecurity maturity model (free) |
| GDPR / CCPA/CPRA | Regulatory text (free) |

## Key Papers

- SMB Cybersecurity Challenges (2023) — *IEEE Access*. 500+ SMBs: 87% no dedicated security staff
- Automated Compliance Framework (2022) — *J Cybersecurity and Privacy*
- Lallie et al. (2021) — "Cyber security in the age of COVID-19" — *Computers & Security*
- CMMC Analysis (2024) — *J Strategic Security*. SMB defense contractor burden
- AI for Regulatory Compliance Review (2023) — *Artificial Intelligence and Law*

## Open Source Adjacencies

- [Comp AI](https://github.com/trycompai/comp) — AGPLv3, SOC 2/ISO 27001/GDPR. Most mature OS compliance tool
- [Probo](https://github.com/getprobo/probo) — MIT, Go GRC with MCP API
- [Bubba AI](https://bubba.ai) — SOC 2/ISO 27001 for startups
- [OpenSCAP](https://github.com/OpenSCAP) — NIST-certified security automation

## Skills Needed

- Regulatory knowledge (GDPR, CCPA, HIPAA, CMMC, PCI-DSS)
- Full-stack web dev (React + Python/FastAPI)
- API integration (Google Workspace, QuickBooks, Shopify)
- Document generation (PDF forms)
- LLM integration (policy writer)

## Risks

- Comp AI has strong momentum — need differentiation on SMB breadth not startup depth
- SMBs are notoriously low-spending on software
- Compliance ≠ security — risk of false sense of security
- Fast-changing regulations = ongoing maintenance burden
- MSSPs bundle compliance for $500-5K/month
