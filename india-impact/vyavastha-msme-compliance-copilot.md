---
track: india-impact
status: published
---

# Vyavastha — MSME Compliance Copilot

> "India's 6.45 crore MSMEs face 1,450+ regulatory obligations, 77+ licenses to start a business, and compliance costs of ₹13–17 lakh per year. This 'regulatory cholesterol' creates the missing middle — firms that never grow because compliance becomes unmanageable."

## The Problem

India has 64.5 million micro, small, and medium enterprises (MSMEs), employing approximately 110 million workers and contributing 30% of GDP and 45% of manufacturing output. Yet these enterprises face an extraordinary regulatory burden: over 1,450 distinct regulatory obligations spanning central and state laws, 77+ licenses required just to begin operations, 59 types of government inspectors, and an average of 42 legal updates published every single day.

This "regulatory cholesterol" — as former NITI Aayog CEO Amitabh Kant described it — creates a structural barrier to growth. Small firms hit a compliance wall as they scale, and many choose to stay informal or small rather than navigate the complexity. The cost of compliance (₹13-17 lakh/year) is itself part of the problem: hiring a chartered accountant or compliance firm costs about the same as the compliance burden itself, creating a regressive tax on small businesses.

Existing solutions serve either large enterprises (who can afford ₹50L+/year compliance suites) or provide isolated registrations (government portals for Udyam, GST, EPFO — each separate, each painful). No solution exists that gives the small business owner a single AI-powered assistant who understands their entire compliance picture, automates form filling, tracks deadlines across all regulators, and proactively warns them of changes.

## Why Existing Solutions Fail

| Approach | Limitation |
|----------|-----------|
| TeamLease RegTech | Enterprise-focused; costs ₹50L+/year — out of reach for MSMEs |
| CA firms / compliance consultants | ₹13-17L/year recurring cost — the problem IS the cost of compliance |
| Government portals (NSWS, Udyam, GST) | Registration-only; no ongoing compliance calendar or monitoring |
| Legal consultants | Reactive (crisis-driven) rather than proactive and preventative |
| ERP / accounting software (Tally, Zoho) | Financial compliance only; no regulatory awareness or license tracking |
| WhatsApp / Telegram groups | Manual, noisy, unreliable, no personalisation |

## What to Build

- **MSME registration wizard**: Unified one-click registration (Udyam + GST + EPFO + ESIC + Professional Tax) via DigiLocker/Aadhaar
- **Compliance calendar**: Personalised calendar of all upcoming returns, renewals, inspections, and deadlines
- **Auto-form filling**: Top 50+ government forms auto-filled via DigiLocker (name, address, Aadhaar, PAN, bank)
- **Regulatory change monitor**: 42 daily legal updates filtered by business type, state, and industry
- **License expiry tracker**: Proactive reminders 60/30/7 days before license renewal dates
- **Penalty risk scoring**: "Your factory licence expires in 5 days — ₹10,000/day penalty if you miss it"
- **Inspector preparation assistant**: Checklist and document pack for upcoming government inspections
- **Labour law compliance module**: ESI, PF, Bonus, Gratuity, Contract Labour — automated calculation and filing

**MVP time estimate**: 12-16 weeks

## Stakeholders & Users

- **6.45Cr** MSMEs registered in India (99% micro)
- **~11Cr** workers employed by MSMEs
- **30%** of India's GDP contributed by MSMEs
- **45%** of India's manufacturing output
- All 29 states and 7 UTs (state-level compliance variation)

## Data Sources

| Source | Description |
|--------|-------------|
| [NSWS API](https://www.nsws.gov.in/) | National Single Window System — portal for business registrations |
| [GST Portal](https://www.gst.gov.in/) | GST registration, returns, and compliance data |
| [EPFO API](https://www.epfindia.gov.in/) | Employee Provident Fund Organisation registrations and filings |
| [ESIC API](https://www.esic.gov.in/) | Employee State Insurance Corporation compliance |
| [MCA21](https://www.mca.gov.in/) | Ministry of Corporate Affairs company registration and filings |
| [State Udyam Portals](https://udyamregistration.gov.in/) | MSME registration and classification |

## Key Papers

1. TeamLease RegTech (2025). *Decoding Compliance: MSME Regulatory Burden in India*.
2. NITI Aayog (2024). *Reducing Compliance Burden: A State-Level Analysis*. Government of India.
3. DPIIT (2025). *Business Reforms Action Plan 2025-26*. Department for Promotion of Industry and Internal Trade.
4. Kant, A. (2024). *60,000 Compliances: The Story of India's Regulatory Cholesterol*. NITI Aayog Blog.
5. Policy Circle (2025). *Cost of Compliance in India: An MSME Survey Report*.

## Open Source Adjacencies

- [India Compliance API Wrappers](https://github.com/indiacompliance/) — Community wrappers for GST, EPFO, ESIC APIs
- [GST Sahay](https://github.com/gstsahay/) — Open-source GST filing assistant
- [NSWS Integration SDKs](https://www.nsws.gov.in/docs/) — Government-provided API SDKs for single-window clearance

## Success Criteria

- [ ] One-click MSME registration (Udyam + GST + EPFO + ESIC) in under 10 minutes
- [ ] Cover top 5 business types (retail, manufacturing, restaurant, transport, services)
- [ ] 90% auto-fill accuracy for DigiLocker-based form fields
- [ ] Track 500+ compliance deadlines across central and state regulators
- [ ] Regulatory change monitor with 95%+ precision on relevant updates

## Skills Needed

- Government API integration (NSWS, GST, EPFO, ESIC, MCA21)
- DigiLocker / Aadhaar OAuth consent flow
- LLM for form drafting and compliance document generation
- React / Next.js (web-first, mobile-responsive)
- Python backend (FastAPI / Django) for rule engine
- Database design for multi-regulator compliance calendar

## Risks

- Government APIs change frequently and without notice — version drift is a maintenance burden
- State-level variation across 29 states means compliance rules differ by jurisdiction
- MSME software adoption is low — most micro-enterprises operate informally with no digital workflow
- Pricing model must be affordable (₹500-2000/month) while delivering real value
- Many MSMEs operate in the informal economy — reaching them is a distribution challenge
- Competition from CA firms (who see compliance as their core revenue stream)
