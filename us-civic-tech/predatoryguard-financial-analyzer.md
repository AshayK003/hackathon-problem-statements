---
track: us-civic-tech
status: published
---

# PredatoryGuard — Consumer Financial Product Analyzer

> Every day, millions of Americans receive predatory loan offers. The CFPB has 3.2M+ complaints. No one is connecting the data to protect consumers. Yet.

## The Problem

Predatory lending is a national crisis hiding in plain sight. **Payday loans, title loans, rent-to-own schemes, earned-wage advances, and buy-now-pay-later traps** target vulnerable consumers — low-income families, seniors, veterans, and communities of color.

The scale is staggering: **5.8 million fraud complaints** were filed with the FTC in 2024 alone, representing **$10 billion+ in losses**. The **CFPB Consumer Complaint Database** contains **3.2 million+ records** — a treasure trove of real-world evidence about bad actors. Yet **no consumer-facing tool uses this data proactively** to protect people before they sign.

Consumers receive offers daily — mail, email, text, in-store — with APRs that legally qualify as usurious (averaging 300–600% APR). They must decode complex TILA (Truth in Lending Act) disclosures, compare effectively-hidden terms, and research company reputations — all while under financial pressure.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| CFPB complaint database | Raw data dump; no consumer-facing analysis or alerting |
| FTC Consumer Sentinel | Internal law enforcement tool; not available to consumers |
| Credit counseling agencies | Reactive (post-debt); limited to debt management |
| NerdWallet / Bankrate | General financial education; no offer-specific analysis |
| Consumer Reports | Product reviews; no real-time offer evaluation |
| BBB / Trustpilot | Easily gamed; no regulatory complaint data integration |
| **No proactive consumer tool exists** | Zero products that analyze offers before consumers sign |

## What to Build

A consumer-facing financial product analyzer that:

- **Analyzes any loan or credit offer** — user uploads/pastes terms; tool calculates real APR, total cost, hidden fees
- **Checks company reputation** against CFPB complaint database, FTC actions, state AG enforcement
- **Detects red flags** — common predatory indicators (balloon payments, mandatory arbitration, single-premium credit insurance)
- **Explains TILA disclosures in plain English** — what your "APR" really means in dollars
- **Recommends alternatives** — credit unions, CDFIs, nonprofit alternatives
- **Generates complaints** — pre-filled CFPB, FTC, or state AG complaint forms
- **Tracks company enforcement history** — ongoing lawsuits, settlements, consent orders

**MVP (6–8 weeks solo):** PDF/text offer analysis + CFPB database lookup + red-flag detection + plain-language explanation. Single-user web tool. This is the fastest MVP in the track.

## Stakeholders

- **300M+ consumers** targeted by financial product offers
- **50M+ people** targeted by predatory loan offers annually
- **26M seniors** (disproportionately targeted)
- **Veterans and military families** (targeted by predatory lenders near bases)
- **CFPB, FTC, state AGs** (enforcement agencies needing consumer tools)
- **Community development financial institutions (CDFIs)**

## Data Sources

| Source | Description |
|---|---|
| [CFPB Consumer Complaint Database](https://www.consumerfinance.gov/data-research/consumer-complaints/) | 3.2M+ complaints with company names, products, issues |
| [FTC Consumer Sentinel](https://www.ftc.gov/enforcement/consumer-sentinel-network) | 5.8M+ fraud reports (2024) |
| [HMDA (Home Mortgage Disclosure Act)](https://www.consumerfinance.gov/data-research/hmda/) | Mortgage lending patterns, redlining detection |
| [NCSL Usury Laws](https://www.ncsl.org/financial-services/state-usury-laws) | State-by-state interest rate caps |
| [CFPB Enforcement Actions](https://www.consumerfinance.gov/enforcement/) | Ongoing and settled enforcement cases |

## Key Papers

- CFPB (2024) — Annual report on predatory lending
- Federal Reserve (2023) — Predatory lending and financial inclusion
- FTC (2024) — Consumer Sentinel Network Data Book
- National Consumer Law Center — Payday and title loan state laws
- Pew Charitable Trusts — Payday lending facts and reforms

## Open Source Adjacencies

- [CFPB Open Source Tools](https://github.com/cfpb) — Multiple consumer protection tools
- [HMDA Explorer](https://ffiec.cfpb.gov/data-browser/) — Mortgage lending data browser
- [complaint-database-client](https://cfpb.github.io/api/ccdb/) — CFPB complaint DB API client
- regtech-api — Regulatory tech APIs

## Success Criteria

- Analyze a typical payday loan offer in under 10 seconds (photo → report)
- Match company against CFPB database with >90% accuracy
- Detect all standard predatory indicators (balloon payments, arbitration clauses, etc.)
- Generate a CFPB-complaint-ready form in under 30 seconds
- Save users an estimated $500+ per avoided predatory loan

## Skills Needed

- **Python/Node.js** backend
- **LLM + OCR** (document parsing, plain-language translation)
- **Financial domain knowledge** (TILA, APR calculation, loan structures)
- **React/TypeScript** for consumer UI
- **API integration** (CFPB, FTC, state AG databases)
- **Data engineering** (3.2M+ complaint records — indexing, search, dedup)

## Risks

- **Company name matching:** CFPB database has messy company names. Fuzzy matching needed.
- **Legal accuracy:** Must correctly interpret TILA disclosures. Consult with consumer protection attorneys.
- **Business model:** Free for consumers. Potential B2B with legal aid orgs, CFPB, or CDFIs.
- **False positives/negatives:** Over-flagging undermines trust; under-flagging harms users. Rigorous testing needed.
- **Offer variability:** Loan terms come in many formats. OCR quality will vary. Build for gradual improvement.
