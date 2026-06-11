---
track: us-civic-tech
status: published
---

# FOIAbot — Intelligent Public Records Request Assistant

> Public records belong to the people. Accessing them shouldn't require a law degree, six months of waiting, and a spreadsheet of deadlines.

## The Problem

The Freedom of Information Act (FOIA) and its state equivalents guarantee public access to government records. In theory. In practice, requesting records is a slow, adversarial, expertise-intensive process.

**Nearly 1 million federal FOIA requests** are filed every year, plus **50 million+ state-level requests**. Journalists spend months of back-and-forth per request — agency shopping, appealing denials, negotiating fee waivers, and tracking response times across different jurisdictions. **72% of requests target law enforcement**, the most resistant agencies. Common outcomes: "no records found," excessive fees, years-long delays, or release of useless boilerplate.

Each jurisdiction has different deadlines, exemptions, fee structures, and appeal processes. There's no centralized assistant to help requesters draft better requests, target the right agency, track deadlines, or fight denials — even though the law says the records belong to the people.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| MuckRock | Drupal-based; great for filing but no AI assistance; manual drafting, no smart agency targeting |
| FOIA Machine | Unmaintained; basic tracking only |
| Do-it-yourself | Months of research per request; most first-time requesters give up |
| Commercial FOIA services | $200–500/hour for attorneys; unaffordable for journalists and citizens |
| Agency FOIA websites | Designed to minimize agency burden, not to help requesters; confusing, inconsistent |

## What to Build

An intelligent public records assistant that:

- **Drafts smart FOIA requests** — suggests optimal scope, jurisdiction-specific framing, and language that reduces denial risk
- **Targets the right agency** — given a topic, identifies which federal/state/local agencies hold responsive records
- **Tracks deadlines** automatically across federal (20 business days) and all 50 state FOIA laws
- **Generates appeals** with proper legal citations for each exemption category
- **Negotiates fee waivers** — drafts public-interest fee waiver language that succeeds
- **Analyzes responses** — flags boilerplate/non-responsive language, suggests follow-ups
- **Suggests document filing** — prepares releases for DocumentCloud

**MVP (6 weeks solo):** Request drafting assistant + agency targeting + deadline tracker for federal FOIA only. State expansion post-MVP.

## Stakeholders

- **250,000+ journalists** who file FOIA requests regularly
- **Every citizen** who has the right to access public records
- **Advocacy organizations** (ACLU, EFF, transparency watchdogs)
- **Academic researchers** studying government operations
- **Pro se litigants** seeking discovery materials

## Data Sources

| Source | Description |
|---|---|
| [MuckRock API](https://www.muckrock.com/api/) | 500K+ real FOIA requests and responses |
| [FOIAonline](https://foiaonline.regulations.gov/) | Multi-agency FOIA portal |
| [DOJ FOIA Annual Reports](https://www.justice.gov/oip/freedom-information-act-annual-reports) | Agency-level FOIA performance data |
| [Reporters Committee FOIA Wiki](https://foia.wiki/) | Legal guidance per jurisdiction |
| [DocumentCloud](https://www.documentcloud.org/) | 10M+ public documents (post-release) |
| [FOIA.gov](https://www.foia.gov/) | Agency contact info and statistics |

## Key Papers

- Cuillier (2019) — The future of FOIA: technology and transparency
- Micinski (2021) — Machine learning for FOIA request optimization
- Kwoka (2018) — Saving the Freedom of Information Act (FOIA Inc.)
- Reporters Committee for Freedom of the Press — FOIA litigation guide

## Open Source Adjacencies

- [MuckRock](https://github.com/MuckRock/muckrock) — Drupal-based FOIA filing platform (full-stack)
- [FOIA Machine](https://foiamachine.com/) — basic tracking (unmaintained)
- [DocumentCloud](https://github.com/danlamanna/documentcloud) — document management
- [foia.gov developer resources](https://www.foia.gov/developer.html) — API docs

## Success Criteria

- Draft a complete FOIA request from a one-sentence description in under 30 seconds
- Recommend the correct agency with >90% accuracy for federal requests
- Track all deadlines correctly across federal + 5 pilot states
- Generate appeal letter with valid statutory citations that passes attorney review
- Achieve 2x success rate for fee waiver requests vs. baseline

## Skills Needed

- **Python/Node.js** backend with API integrations
- **LLM integration** for drafting and analysis (GPT/Claude + prompt engineering)
- **Legal knowledge base** (FOIA statutes, exemptions, case law)
- **React/TypeScript** for the web UI
- **Calendar/timezone management** (50+ jurisdiction deadline engine)
- **Document management** (DocumentCloud API, PDF processing)

## Risks

- **Agency hostility:** Some agencies may block automated request filing. Work with transparency orgs on strategy.
- **Legal accuracy:** Appeal and fee-waiver language must be legally sound. Build in human-review workflows.
- **Jurisdiction maintenance:** State FOIA laws change. Community-contributed updates essential.
- **Scope management:** FOIA + 50 states is enormous. Doubly down on federal + 5 pilot states for MVP.
- **Ethical use:** Could be used for harassment. Design safeguards: rate limits, transparency, terms of service.
