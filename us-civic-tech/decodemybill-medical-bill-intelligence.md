---
track: us-civic-tech
status: published
---

# DecodeMyBill — Consumer Medical Bill Intelligence

> 80% of medical bills contain errors. The system is designed to be impenetrable. Your doctor saved your life — the billing department shouldn't get to bankrupt you.

## The Problem

The US healthcare system is notorious for its billing complexity. **80% of medical bills contain errors.** Every year, **$262 billion in claims are denied**. Yet only **0.2% of patients appeal** — and those who do win **40–70% of the time**.

The problem isn't just the errors — it's that patients literally cannot understand their bills. Medical bills are written in CPT (Current Procedural Terminology) and DRG (Diagnosis-Related Group) codes — an alphanumeric language designed for insurance processing, not patient comprehension. Fees are disconnected from any visible price list. Line items like "Level 3 Emergency Visit" or "Surgical Pathology — Level IV" are meaningless to the average person.

**66% of all bankruptcies** involve medical debt. **100M+ Americans** carry medical debt. The system is broken not because prices are high (though they are), but because it's impossible for patients to know what they should pay, whether charges are correct, or how to fight back.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| Hospital billing departments | Conflict of interest — they want you to pay; no incentive to help you audit |
| Insurance EOB (Explanation of Benefits) | Confusing, designed for their own accounting, not for patient understanding |
| Medical billing advocates | $100–300/hour; unaffordable for most patients with medical debt |
| Google/forums | Guesswork; no access to fee schedules or pricing data |
| Cash-pay price estimators | Only for uninsured; don't help audit existing bills |
| HealthSherpa / GoodRx | Shopping tools only; nothing for existing bills or appeals |

## What to Build

An AI-powered medical bill intelligence platform that:

- **Parses any medical bill via OCR + LLM** — extracts codes, charges, dates, provider details
- **Detects errors** by cross-referencing CMS fee schedules, Medicare reimbursement rates, and facility-specific chargemasters
- **Translates billing codes to plain English** — "This is a charge for a chest X-ray with radiologist interpretation"
- **Generates appeal letters** with specific regulatory citations (No Surprises Act, state balance billing laws, CPT coding rules)
- **Provides negotiation scripts** — what to say on the phone, what to ask for, what to cite
- **Compares prices** for the same service across facilities in your area
- **Estimates what you should pay** based on insurance type, out-of-network status, and state regulations

**MVP (10–12 weeks solo):** OCR bill parsing + code-to-plain-English translation + error detection against CMS fee schedules for top 100 CPT codes. Single-user web app.

## Stakeholders

- **300M+ insured Americans** who receive medical bills
- **100M+ people with medical debt**
- **66% of US bankruptcies** involving medical debt
- **Self-pay and uninsured patients** with no price protection
- **Patient advocacy organizations**

## Data Sources

| Source | Description |
|---|---|
| [CMS Hospital Price Transparency](https://www.cms.gov/hospital-price-transparency) | Hospital chargemasters and negotiated rates |
| [CMS Physician Fee Schedule](https://www.cms.gov/medicare/physician-fee-schedule) | Medicare reimbursement rates for procedures |
| [FAIR Health](https://www.fairhealth.org/) | Private insurer reimbursement benchmarks |
| [HealthCare Bluebook](https://www.healthcarebluebook.com/) | Fair price estimates for medical services |
| [No Surprises Act resources](https://www.cms.gov/nosurprises) | Federal surprise billing protections |

## Key Papers

- Health Affairs (2023) — 80% error rate in hospital billing study
- JAMA (2021) — Patient comprehension of medical billing codes
- KFF (2024) — Medical debt in the United States
- Consumer Financial Protection Bureau (2022) — Medical debt credit reporting

## Open Source Adjacencies

- [hospital-price-transparency](https://github.com/ropensci/hospitalprice) — R package for hospital pricing
- [Py-Medical-Code](https://github.com/smwaaver/py-medical-code) — CPT/HCPCS code processing
- [healthcareai-py](https://github.com/HealthcareAI/healthcareai-py) — ML for healthcare

## Success Criteria

- Parse and decode a typical emergency room bill in under 60 seconds
- Detect overcharges with >90% accuracy vs. professional medical billing audit
- Generate a valid appeal letter accepted by at least 2 major insurers in testing
- Translate a bill from all CPT/DRG codes to plain English readable at 8th-grade level
- Save users an average of $500+ per audited bill

## Skills Needed

- **Python** (FastAPI, OCR pipelines)
- **LLM + OCR** (Tesseract/document parsing, GPT-4/Claude for code translation)
- **Healthcare domain knowledge** (CPT, DRG, ICD-10, revenue codes)
- **Regulatory knowledge** (No Surprises Act, state balance billing laws)
- **React/TypeScript** for the consumer-facing UI
- **CMS data parsing** (machine-readable price transparency files)

## Risks

- **Data inconsistency:** CMS price transparency files are inconsistent across hospitals; parsing is hard
- **Regulatory landscape varies by state:** Balance billing rules differ enormously; need a state rules engine
- **LLM hallucination:** Must verify every fee schedule comparison; cannot trust LLM to do math
- **User trust:** Medical bills are stressful; the tool must be careful, accurate, and reassuring
- **Privacy:** Medical billing data is PHI. HIPAA compliance needed if storing patient data. Consider local-first architecture.
