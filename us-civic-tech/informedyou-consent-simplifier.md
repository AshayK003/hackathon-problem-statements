---
track: us-civic-tech
status: published
---

# InformedYou — Clinical Trial Consent Simplifier

> Clinical trial consent forms are written at college reading level. The average US adult reads at 8th grade. 2.5 million people sign these forms every year without understanding what they're agreeing to.

## The Problem

Informed consent is the ethical foundation of clinical research. But there's a fundamental problem: **the documents aren't actually understood by the people signing them.**

Informed Consent Forms (ICFs) for clinical trials are written at a **Flesch-Kincaid grade level of 14–16** — college-level reading. The average US adult reads at an **8th-grade level**. Only **5% of ICFs** meet the FDA's own recommendation for readability.

Every year, **2.5 million+ people** participate in clinical trials. They sign forms that describe risks, benefits, alternatives, and procedures — in language they cannot fully parse. The result isn't just a paper problem: it's an ethical and regulatory failure. Patients cannot give truly informed consent if they don't understand what they're consenting to.

Beyond readability: ICFs are dense, lengthy (15–20 pages typical), full of passive voice and legal hedging, and formatted in ways that bury key information. Non-English speakers face additional barriers, as ICF translation quality varies enormously.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| Current ICFs by IRBs/institutions | Written by lawyers and doctors for lawyers and doctors, not patients |
| OpenTrials / ClinicalTrials.gov | Trial registration only; no consent form access or analysis |
| Readability checkers (Flesch-Kincaid) | Score-only; don't simplify or restructure actual content |
| Google Translate / machine translation | Not medical-grade; dangerous for consent documents |
| Consent researcher tools | Academic projects; no production-ready deployments |
| **No tool simplifies ICFs while preserving legal disclosures** | Core gap: accuracy vs. accessibility |

## What to Build

An AI-powered consent form simplifier that:

- **Simplifies ICF language** to target reading levels (8th grade, 6th grade, Spanish, etc.) while preserving every legally-required disclosure
- **Extracts key information** into structured summaries: purpose, risks, benefits, alternatives, costs, duration
- **Generates comprehension-check questions** — tests whether the participant truly understands key points
- **Creates risk/benefit comparison tables** — what are the risks, how likely, how severe; what are the alternatives
- **Builds timeline visualization** — study schedule with visits, procedures, and commitments
- **Adapts for cultural context and language** — not just translation but culturally-appropriate simplification
- **Validates against original** — ensures no simplified version omits or distorts required disclosures
- **Outputs FDA-compliant simplified ICF** ready for IRB submission

**MVP (6 weeks solo):** ICF upload → LLM simplification to 8th-grade level + key info extraction + comprehension check questions. Web app + API.

## Stakeholders

- **2.5M+ clinical trial participants/year** who deserve to understand what they're signing
- **350M+ US population** — everyone will encounter some form of medical consent
- **IRBs (Institutional Review Boards)** — need tools to approve readable ICFs
- **Clinical research organizations (CROs)** — responsible for participant enrollment
- **Pharmaceutical companies** — regulatory requirement for understandable consent
- **FDA** — draft guidance (2023) emphasizes plain language in ICFs
- **Patient advocacy groups** — fighting for health literacy and patient rights

## Data Sources

| Source | Description |
|---|---|
| [ClinicalTrials.gov](https://clinicaltrials.gov/) | 450K+ registered trials with protocol details |
| [FDA Informed Consent Guidelines](https://www.fda.gov/regulatory-information/search-fda-guidance-documents/informed-consent) | 21 CFR 50, ICH GCP E6 |
| [NCI Plain Language Glossary](https://www.cancer.gov/publications/dictionaries/cancer-terms) | Medically-accurate plain language definitions |
| [MedlinePlus](https://medlineplus.gov/) | Consumer-friendly medical information |
| [FDA Draft Guidance (2023)](https://www.fda.gov/regulatory-information/search-fda-guidance-documents/informed-consent-guidance) | Plain language recommendations |

## Key Papers

- Paasche-Orlow et al. (2021) — Readability of consent forms (JAMA Internal Medicine)
- Tamariz et al. (2022) — Health literacy and informed consent
- FDA (2023) — Draft guidance on informed consent readability
- AMA — Health literacy and patient safety recommendations
- National Academies — Health literacy framework for informed consent

## Open Source Adjacencies

- [OpenTrials](https://github.com/opentrials/opentrials) — Open clinical trial data
- [readability-nlp](https://github.com/cdimascio/py-readability-metrics) — Readability scoring libraries
- EasyDNN — Text simplification research
- [ClinGen](https://clinicalgenome.org/) — Clinical genomics consent resources

## Success Criteria

- Simplify a standard 15-page ICF to 8th-grade reading level in under 60 seconds
- Preserve 100% of FDA-required disclosure elements (validated against checklist)
- Achieve >95% comprehension score when tested with lay readers (vs. <50% for original ICF)
- Generate IRB-ready simplified ICF that passes legal review in pilot test
- Support English and at least one additional language (Spanish)

## Skills Needed

- **Python/LLM orchestration** (GPT-4/Claude for text simplification)
- **NLP/NLG** (text simplification, readability evaluation, paraphrasing with constraints)
- **React/TypeScript** for the web UI
- **Medical/regulatory domain knowledge** (FDA consent regulations, IRB requirements)
- **Evaluation methodology** (user comprehension testing, expert review protocols)
- **PDF/text extraction** (parsing existing ICF formats)

## Risks

- **Regulatory liability:** Simplified ICFs must be legally equivalent to originals. Must include prominent disclaimer and IRB-review instructions.
- **Simplification accuracy:** Must never distort risk information. "Loss of limb" cannot become "small chance of injury." Conservative simplification is mandatory.
- **Domain complexity:** Some medical concepts resist simplification (genetic risk, complex pharmacology). Determine which ICFs are in-scope.
- **Adoption barrier:** IRBs are risk-averse. Need validation studies and FDA-reference implementations to build trust.
- **Evaluation challenge:** "Understanding" is hard to measure. Need validated comprehension assessment tools alongside the simplifier.
