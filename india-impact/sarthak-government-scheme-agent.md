---
track: india-impact
status: published
---

# Sarthak — Government Scheme Discovery Agent

> "India has 740+ central schemes and thousands of state-level ones with a combined budget of ₹7.67 lakh crore. Most eligible citizens never apply. Studies show the average household is aware of only 2–3 schemes out of 20+ they qualify for."

## The Problem

India's social welfare system is one of the largest in the world, with over 740 centrally-sponsored schemes spanning food security, education, healthcare, housing, pensions, skill development, and entrepreneurship. The combined central outlay exceeds ₹7.67 lakh crore annually, and state-level schemes add thousands more. In principle, these programmes should cover every vulnerable Indian. In practice, most eligible citizens never receive the benefits they are entitled to.

The fundamental problem is discovery. Studies of India's welfare ecosystem consistently show that the average household knows about only 2-3 schemes out of 20 or more they are eligible for. The information exists — on myScheme.gov.in, India.gov.in, and state portals — but it is fragmented, presented as exhaustive lists rather than personalised recommendations, available only in English or Hindi, and requires applicants to navigate separate application forms, separate verification processes, and separate renewal cycles for each scheme.

The government's own myScheme.gov.in portal took a step in the right direction by creating a central directory with a filter-by-category interface. But it is a static catalogue, not an intelligent agent. It does not proactively tell a household that "Your family qualifies for 14 schemes worth ₹2.3L/year" — and crucially, it cannot detect life events (turning 60 means pension eligibility, having a girl child means Sukanya Samriddhi, losing a job triggers skill benefits). This is the perfect use case for an AI agent layer on top of India's existing DPI.

## Why Existing Solutions Fail

| Approach | Limitation |
|----------|-----------|
| myScheme.gov.in | Static category filter; no AI, no eligibility reasoning, no alerts |
| India.gov.in | Exhaustive list — no personalisation, no eligibility check |
| CSC (Common Service Centres) | Operator-dependent access; 50+ average age of operators; reach limited |
| State government portals | Siloed, fragmented, no cross-scheme recommendation |
| WhatsApp community groups | Manual sharing; no verification, no personalisation, no renewals |
| NGO outreach campaigns | Limited to specific geographies and scheme categories |
| Bank Mitra / CSV operators | Focused on financial inclusion, not scheme discovery |

## What to Build

- **Personalised eligibility detection**: "Tell us about yourself" wizard (8 questions, WhatsApp-first) → list of eligible schemes ranked by estimated annual benefit
- **Life-event triggers**: Proactive detection: 60th birthday → pension schemes; girl child birth → Sukanya Samriddhi; unemployment → DDU-GKY/CSC skill training; crop loss → PMFBY claim
- **Multi-lingual application assistant**: Guided form-filling in Hindi + 5 regional languages with DigiLocker document auto-fill
- **Benefit calculator**: "Your family qualifies for ₹2.3 lakh/year across 14 schemes — here's what you're missing"
- **Status tracking**: Track application status across multiple schemes from a single dashboard
- **Renewal reminders**: SMS/WhatsApp 30 days before renewal deadline with one-click renewal
- **Grievance routing**: If scheme benefits are delayed, auto-generate and route grievance to correct department
- **Eligibility change detection**: As family composition or income changes, re-scan eligible scheme set

**MVP time estimate**: 8-10 weeks

## Stakeholders & Users

- **~800M+** PDS (Public Distribution System) beneficiaries
- **~200M+** households potentially eligible for at least one welfare scheme
- **740+** centrally-sponsored schemes across all ministries
- All ministries (Rural Development, Health, Education, Social Justice, etc.)
- Panchayati Raj Institutions (2.6 lakh village panchayats)
- CSC operators (~5 lakh across India)
- NGOs working on social welfare delivery

## Data Sources

| Source | Description |
|--------|-------------|
| [myScheme.gov.in](https://www.myscheme.gov.in/) | Central directory of all government schemes with eligibility criteria |
| [DigiLocker API](https://www.digilocker.gov.in/) | Digital document wallet for auto-filling applications |
| [Aadhaar API](https://uidai.gov.in/) | Consent-based identity verification for benefit eligibility (consent required) |
| Ration card databases | State-level PDS beneficiary lists (API varies by state) |
| SECC 2011 | Socio-Economic and Caste Census — household deprivation data |
| [NFHS Surveys](https://rchiips.org/nfhs/) | National Family Health Survey — demographic and welfare data |
| State scheme portals | State-specific welfare portals (varies by state) |
| [Udyam Registration](https://udyamregistration.gov.in/) | MSME registration for scheme eligibility |

## Key Papers

1. NeGD (2024). *myScheme Architecture: One-Stop Access for Government Schemes*. National e-Governance Division, MeitY.
2. Dreze, J. & Sen, A. (2023). *Hunger and Public Action: India's Welfare Challenge*. Oxford University Press.
3. World Bank (2023). *Social Protection in India: A Review*. World Bank Group Social Protection Series.
4. NITI Aayog (2024). *SDG India Index 2024: Social Welfare and Inclusion*. Government of India.
5. Dreze, J. (2020). *The BSP Approach: Basic Income, Social Protection, and Public Action*. Economic & Political Weekly.

## Open Source Adjacencies

- [OpenFisca](https://openfisca.org/) — Open-source rules engine for tax/benefit simulation (France reference)
- [PolicyEngine](https://policyengine.org/) — US policy simulation engine (design reference)
- [India DPI Stack APIs](https://www.digitalindia.gov.in/) — Aadhaar, DigiLocker, UMANG, UPI APIs
- [OpenBudget India](https://openbudgetsindia.org/) — Open fiscal data on scheme budgets

## Success Criteria

- [ ] Cover 100+ centrally-sponsored schemes in eligibility database
- [ ] Eligibility suggestions with >85% accuracy (validated against scheme rules)
- [ ] WhatsApp response time <5 seconds for eligibility queries
- [ ] Hindi + 5 regional languages supported (English mandatory, others extensible)
- [ ] 1000+ active users in pilot (self-reported scheme discovery/application)

## Skills Needed

- LLM for eligibility reasoning and rule-based matching (Chain-of-Thought prompting)
- OpenFisca-style rules engine (structured eligibility rules for each scheme)
- DigiLocker / Aadhaar consent flow integration
- WhatsApp Business API / Twilio integration
- Multi-lingual NLP (Hindi + 5+ regional languages)
- React / Next.js (web dashboard for scheme administrators)
- Data pipeline for ingesting and updating scheme rules from government portals

## Risks

- Aadhaar consent complexity — requires careful UX and compliance with Data Protection regulations
- Scheme rules change frequently (budget cycles, eligibility revisions, new schemes introduced)
- 740+ central schemes = massive data maintenance burden; manual curation may be needed
- myScheme.gov.in may itself build an AI layer (government MoU risk)
- State-level data inconsistency — state schemes vary wildly in documentation and API availability
- Low digital literacy among target users — WhatsApp-first design is essential but may limit some features
- Benefit leakage / fraud risk — application assistant must not become a tool for fraudulent claims
