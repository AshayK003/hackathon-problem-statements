# 🇺🇸 US Civic Tech

**10 consumer/civic projects** that navigate America's broken regulatory and social systems.

---

## Why This Track

The US has some of the world's most detailed public datasets — and some of the most opaque consumer-facing systems. Medical billing, housing assistance, workers' comp, family court, FOIA, public comments, school funding — every one of these affects millions of people, has public data available, and currently has **no open-source consumer advocate**.

Every opportunity here creates an **AI-powered consumer advocate** for an information-asymmetric system.

## The Problems

| # | Problem | Impact | Novelty | MVP | Why Build It |
|---|---------|--------|---------|-----|-------------|
| 01 | [CivicFeed — Public Comment Intelligence](civicfeed-public-comment-intelligence.md) | 241M citizens, 15K analysts | 9/10 | 6-8w | Democratic participation |
| 02 | [Workers Compass — Claim Navigator](workers-compass-claim-navigator.md) | 5.5M injuries/year | 10/10 | 8-10w | **Most defensible** — zero competitors |
| 03 | [FOIAbot — Public Records Assistant](foiabot-public-records-assistant.md) | 1M+ FOIA requests/year | 9/10 | 6w | Government transparency |
| 04 | [DecodeMyBill — Medical Bill Intelligence](decodemybill-medical-bill-intelligence.md) | 80% of bills have errors | 7/10 | 10-12w | Highest direct $ impact |
| 05 | [ProSe Navigator — Family Court Assistant](prose-navigator-family-court-assistant.md) | 70% self-represented in family court | 8/10 | 8-12w | Access to justice |
| 06 | [PredatoryGuard — Financial Analyzer](predatoryguard-financial-analyzer.md) | $10B+ in scam losses/year | 9/10 | 6-8w | **Fastest MVP** in this track |
| 07 | [UtilityCoach — Energy Assistance Navigator](utilitycoach-energy-assistance-navigator.md) | 1 in 3 US households | 8/10 | 6w | 80% of eligible don't apply |
| 08 | [HousingKey — Housing Program Navigator](housingkey-housing-program-navigator.md) | 20M+ households with worst-case needs | 8/10 | 10-12w | Defining domestic crisis |
| 09 | [InformedYou — Consent Simplifier](informedyou-consent-simplifier.md) | 2.5M+ trial participants/year | 7/10 | 6w | Ethical research |
| 10 | [SchoolEquityWatch — Funding Transparency](school-funding-transparency-analyzer.md) | 50M+ K-12 students | 7/10 | 12-16w | **Best OSS community potential** |

## Quick Start by Goal

| If you want to... | Start with |
|-------------------|-----------|
| Ship the **fastest MVP** | [PredatoryGuard](predatoryguard-financial-analyzer.md) (CFPB API + LLM = 6 weeks) |
| Build the **most defensible** | [Workers Compass](workers-compass-claim-navigator.md) ($50B industry, zero consumer competitors) |
| Max **societal impact** | [CivicFeed](civicfeed-public-comment-intelligence.md) or [ProSe Navigator](prose-navigator-family-court-assistant.md) |
| Build for **open-source community** | [ProSe Navigator](prose-navigator-family-court-assistant.md) or [SchoolEquityWatch](school-funding-transparency-analyzer.md) |
| **Category-create** from scratch | [CivicFeed](civicfeed-public-comment-intelligence.md) or [Workers Compass](workers-compass-claim-navigator.md) |

## Data Sources Referenced

- Regulations.gov API, Federal Register API, CFPB Complaint Database
- CMS Hospital Price Transparency, HUD Picture of Subsidized Households
- BLS, OSHA, MuckRock API, CourtListener API, ClinicalTrials.gov
- NCES Common Core of Data, Census PUMS, HMDA

## Key Risks Across This Track

- **Regulatory** — Legal gray areas for automated filing, UPL (Unauthorized Practice of Law)
- **Adoption** — Target populations often have low digital access
- **Maintenance** — Government data formats and policies change
- **Defensibility** — Some solutions can be replicated by well-funded incumbents
