---
track: india-impact
status: published
---

# Nyaya Sahayak — Court Case Navigator

> "India has 52 million pending court cases with an average resolution time of 13.5 years. Two-thirds are land-related. Most litigants cannot afford lawyers. No consumer-facing tool exists to file a case, track progress, understand legal rights, get hearing alerts, or prepare for court."

## The Problem

India's judicial system is one of the most congested in the world. Over 52 million cases are pending across subordinate courts, high courts, and the Supreme Court, with an average resolution time of 13.5 years. Two-thirds of all pending cases are land and property disputes — a figure that speaks to the intersection of India's opaque land records system and a legal process that can outlive the litigants. Each year, 5 million new cases are added.

The government's eCourt Services platform provides a robust API that allows anyone to look up case status by CNR (Case Number Record) number, view orders, track hearing dates, and access court documents. But this platform is designed for legal professionals — judges, lawyers, court clerks — and is inscrutable to the average citizen. Legal documents are in English or regional legalese, hearing dates are displayed as raw court calendar entries, and no guidance is offered on what to do next.

There is no consumer-facing legal tool that helps a litigant understand their case in plain language, prepare for their next hearing, know what forms to file, calculate timelines, or even discover basic legal rights. Legal aid is available but is criminal-focused and severely overloaded. Existing AI legal tools in India serve lawyers (research, drafting, transcription), not the 52 million litigants who cannot afford a lawyer but still need to navigate the system.

## Why Existing Solutions Fail

| Approach | Limitation |
|----------|-----------|
| eCourt Services | Judge/lawyer-facing UI; raw data, no plain-language interpretation |
| Adalat AI | Courtroom transcription for lawyers, not litigant-facing |
| LawCentral AI | Lawyer tools (research, drafting) — ₹5000+/month |
| Indian LegalGPT | Legal research model — requires legal expertise to operate |
| Legal aid clinics | Overloaded, criminal-only, limited to indigent defendants |
| JustiFlow | Academic prototype; no deployment, no consumer UX |
| Vakilsearch / LegalRaasta | Document filing services — reactive, per-service fee model |

## What to Build

- **Case status in plain language**: Input CNR → output plain English/Hindi summary: "Your case is scheduled for hearing on March 15. The other side has not yet filed their response. The average time for this type of case in your court is 18 months."
- **Daily hearing SMS/WhatsApp alerts**: "Your hearing in Case 123/2023 is tomorrow at 10:30 AM, Court No. 7, Tis Hazari. Judge: Ms. Sharma" — with directions link
- **Document guidance and templates**: Guided form-filling for common applications (bail, caveat, review, execution, transfer petition)
- **Court navigation assistant**: "Court is in the new building, 3rd floor, Room 312. Nearest metro is Dilshad Garden."
- **Timeline prediction**: Based on historical data for the same court, judge, and case type
- **Legal awareness prompts**: "Did you know you can file a caveat to prevent an ex-parte order?" | "Your case has been pending 2+ years — you can apply for early hearing"
- **Multi-lingual interface**: Hindi + 8 Indian languages, all translated from English case data
- **Case diary**: Personalised pocket book with next 10 hearing dates, document checklist, and notes

**MVP time estimate**: 8-12 weeks

## Stakeholders & Users

- **52M+** pending litigants across India
- **5M+** new cases filed every year
- **25,000+** judges across all court levels
- **1.7M+** enrolled lawyers
- **300M+** citizens who may need legal assistance in their lifetime
- All 29 states + 7 UTs (varying court systems and eCourt API maturity)

## Data Sources

| Source | Description |
|--------|-------------|
| [eCourt Services API](https://services.ecourts.gov.in/) | Public API for case status, orders, hearing dates by CNR |
| [ECOURTS District Data](https://districts.ecourts.gov.in/) | District court case information and cause lists |
| [Indian Kanoon](https://indiankanoon.org/) | Largest open database of Indian case law and judgments |
| [National Judicial Data Grid](https://njdg.ecourts.gov.in/) | Aggregate case statistics and pendency metrics |
| [LawCentral API](https://www.lawcentral.in/) | Legal research API (academic access available) |

## Key Papers

1. NITI Aayog (2024). *Strategies for Reducing Pendency in Indian Courts*. Government of India.
2. Vidhi Centre for Legal Policy (2023). *Justice Delivery in India: A Report on Court Infrastructure and Processes*.
3. Dalal, D. & Cheung, J. (2023). *AI in Judicial Systems: A Survey of Applications and Ethical Considerations*. Stanford Journal of Law & Technology.
4. UNODC (2023). *Artificial Intelligence and Access to Justice*. United Nations Office on Drugs and Crime.
5. Agarwal, V. et al. (2024). *Legal Document Summarization in Low-Resource Indian Languages*. ACL 2024.

## Open Source Adjacencies

- [Indian Kanoon](https://indiankanoon.org/) — Open legal data (case law, statutes, judgments)
- [JustiFlow (GitHub)](https://github.com/justiflow/) — Academic open-source legal workflow prototype
- [Indian LegalGPT](https://github.com/IndianLegalGPT/) — Fine-tuned LLM for Indian legal text
- [CourtListener](https://www.courtlistener.com/) — US reference for open-source court data platform

## Success Criteria

- [ ] Case lookup in under 3 seconds (CNR → plain language summary)
- [ ] Plain English summary accurate for 90%+ of cases (validated by legal professional)
- [ ] Hearing alerts delivered <30 minutes after court upload
- [ ] Cover 5 case types (civil, criminal, family, property, consumer)
- [ ] 500+ active users in pilot (self-reported weekly usage)

## Skills Needed

- eCourt API integration and data parsing (JSON → structured case data)
- LLM for legal summarisation and plain-language translation
- Hindi + 8 Indian languages NLP (translation of case data)
- SMS / WhatsApp notification infrastructure
- React / Next.js (mobile-responsive web, proggressive web app)
- Legal domain knowledge (basic court procedure, case types, forms)

## Risks

- eCourt API varies significantly by state — some states have poor data quality or intermittent availability
- Legal liability for incorrect advice — must clearly disclaim and limit scope to information, not "legal advice"
- State fragmentation: 29 states + 7 UTs means 36+ different court systems with different processes
- BNS (Bharatiya Nyaya Sanhita) transition period — laws and codes are in flux
- Language diversity requires translation accuracy in 8+ languages for legal terminology
- Monetisation is difficult — litigants are stressed, not "shopping" for tools
- Existing legal community may view this as encroachment on their domain
