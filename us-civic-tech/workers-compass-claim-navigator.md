---
track: us-civic-tech
status: published
---

# Workers Compass — Injured Worker's Claim Navigator

> Workers' compensation is a $50B industry built to serve insurers, not the 5.5M Americans injured on the job each year. Change that.

## The Problem

Every year, **5.5 million+ workplace injuries** occur in the United States. The workers' compensation system, a **$50 billion industry**, was designed to protect workers — but in practice, it serves insurance carriers. The result is a byzantine, state-specific maze that injured workers must navigate while recovering from injury.

**40% of initial claims contain errors.** Workers must track state-specific deadlines (some as short as 30 days), navigate employer-chosen doctors, decipher complex legal and medical forms, and appeal denials without legal representation. Missteps mean lost benefits, mounting medical bills, and financial ruin — all while recovering from a workplace injury.

The system varies wildly by state: filing deadlines, benefit formulas, medical provider rules, and appeal processes are all jurisdiction-specific. No consumer-facing tool exists to help workers navigate this complexity.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| Insurance carrier portals | Designed for claims adjusters, not injured workers; no plain-language guidance |
| State WC board websites | Fragmented across 50+ jurisdictions; confusing, bureaucratic, non-standardized |
| Personal injury lawyers | Expensive (30–40% contingency); most workers don't qualify or can't afford |
| Employer HR departments | Conflict of interest — employer pays premiums; incentives run against the worker |
| Generic legal aid websites | Outdated, non-personalized, no interactive tools |
| **No consumer competitor exists** | Zero tools designed specifically for injured workers |

## What to Build

An AI-powered claim navigation assistant that:

- **Guides workers step-by-step** based on their state, injury type, and timeline — what to file, when, and how
- **Auto-fills claim forms** from a natural-language interview ("Tell me what happened")
- **Tracks all deadlines** with automatic reminders across state-specific calendars
- **Explains claim status** in plain language — what a denial letter actually means
- **Drafts appeal letters** with proper legal framing and relevant statutes
- **Suggests doctor selection strategy** — which physicians are worker-friendly in your area

**MVP (8–10 weeks solo):** State-specific process navigation for 1–2 states (pick the most complex: CA, NY, or TX) + document auto-fill + deadline tracking. Expand state coverage post-MVP.

## Stakeholders

- **125M+ covered employees** eligible for workers' comp
- **5.5M+ injured workers/year** who file claims
- **2M+ claims denied or underpaid annually** who could benefit from appeals
- **State workers' compensation boards** (50+ jurisdictions)
- **Worker advocacy and legal aid organizations**

## Data Sources

| Source | Description |
|---|---|
| [BLS Survey of Occupational Injuries](https://www.bls.gov/iif/) | National injury data, industries, demographics |
| [OSHA API](https://www.osha.gov/developers) | Safety standards, enforcement data |
| [WCRI Research](https://www.wcrinet.org/) | Workers' comp system benchmarks and AI studies |
| State WC commission websites | Forms, deadlines, benefit calculators per state |
| NSC Injury Facts (2024) | Cost and prevalence data |

## Key Papers

- WCRI (2025) — AI in workers' compensation: opportunities and challenges
- Kognitos (2024) — 40% initial claim error rate analysis
- NSC (2024) — Workers' compensation injury and cost report
- National Academy of Social Insurance — Annual WC benefits report

## Open Source Adjacencies

- **None exist directly.** This is a greenfield space.
- [Docassemble](https://docassemble.org/) — document automation platform (could be used for form generation)
- [FormSwift](https://formswift.com/) — commercial, not open-source; shows demand exists

## Success Criteria

- Complete claim filing success rate from interview → submitted form for a pilot state
- Reduce form errors to <5% (vs. 40% baseline)
- 100% deadline capture accuracy for covered states
- NPS (user satisfaction) > 50 among injured workers in testing
- Legal aid org demo: 3 minutes to generate a complete appeal draft

## Skills Needed

- **Full-stack web development** (React + Python/FastAPI)
- **Document generation** (PDF filling, Docassemble or similar)
- **Legal domain knowledge** (workers' comp law in at least one state)
- **LLM integration** (form auto-fill from natural language, plain-language explanations)
- **Database design** (multi-state rule engine, deadline calendar)
- **UI/UX for vulnerable users** (simple, accessible, multilingual-ready)

## Risks

- **Legal liability:** Must not practice law without authorization. Disclaimers are essential. Partner with legal aid orgs.
- **Data freshness:** State WC forms and deadlines change. Need a maintenance pipeline and community contributions.
- **State fragmentation:** 50+ jurisdictions with independent rules. MVP must prove value in one state first.
- **User trust:** Injured workers are vulnerable; the tool must feel safe and trustworthy. Design matters enormously.
- **Business model:** Free for workers; potential B2B with legal aid orgs, unions, or state agencies.
