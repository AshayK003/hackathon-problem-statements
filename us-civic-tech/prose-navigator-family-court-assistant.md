---
track: us-civic-tech
status: published
---

# ProSe Navigator — Family Court AI Assistant

> 70–80% of family court cases have at least one self-represented litigant. The system was designed for lawyers. Level the playing field.

## The Problem

Family court is the most common point of contact between Americans and the judicial system — and the least forgiving to those without a lawyer. **70–80% of family court cases** involve at least one self-represented ("pro se") litigant. **15 million+ cases** are filed annually covering divorce, child custody, child support, domestic violence protection orders, and parental rights.

**86% of low-income litigants** receive inadequate or no legal help. Legal aid organizations are chronically underfunded and can serve only a fraction of those who qualify. The result: parents lose custody of their children not because they're unfit, but because they filed the wrong form, missed a deadline, or couldn't articulate the right legal argument.

Court forms are written at college reading level. Procedures vary by county within states. Filing deadlines are strict and unforgiving. Self-represented litigants don't know what they don't know — and the system penalizes that ignorance harshly.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| Legal aid attorneys | Serve <20% of eligible low-income population; massive shortage |
| Court self-help centers | Limited hours, long wait times, no remote access |
| Docassemble / A2J Author | Form assembly only; no guidance on strategy, deadlines, or hearing prep |
| LawHelp.org / state court websites | Static information; no personalization or interactivity |
| Commercial legal software (e.g., LegalZoom) | Document generation only; no procedural guidance |

## What to Build

A procedurally-guided family court assistant that:

- **Conducts a legal assessment diagnostic** — asks targeted questions, identifies the user's situation and legal needs
- **Assembles court forms from natural language** — "I want to file for custody of my 5-year-old" → complete, court-ready forms
- **Manages all deadlines** — automatic calendar based on case type, jurisdiction, and filing date
- **Provides hearing prep checklists** — what to bring, what to say, what the judge will ask
- **Organizes evidence** — guides users to collect and organize relevant documents, texts, emails, financial records
- **Interprets court orders** — plain-language explanation of what a custody order or support order actually means
- **Generates filing instructions** — where to file, how to serve, what comes next

**🚨 CRITICAL: This tool provides procedural guidance only — NOT legal advice. No legal recommendations, no prediction of outcomes, no representation. Every page includes disclaimers. Built for partner review with legal aid organizations.**

**MVP (8–12 weeks solo):** Custody and divorce form assembly + deadline tracking for one state. Hearing prep checklists. Focus on Texas or California as initial state.

## Stakeholders

- **15M+ family court cases filed annually**
- **50M+ people** affected by family court proceedings
- **86% of low-income litigants** without adequate legal help
- **Legal aid organizations** nationwide (LSC-funded, IOLTA-funded)
- **State court administrators** looking to improve access to justice
- **Pro bono attorneys** needing tools to serve more clients

## Data Sources

| Source | Description |
|---|---|
| [CourtListener API](https://www.courtlistener.com/api/) | Millions of federal and state court opinions |
| [RECAP](https://www.courtlistener.com/recap/) | 10M+ PACER documents (free access to federal dockets) |
| [LII / Cornell Legal Information Institute](https://www.law.cornell.edu/) | Open-access legal definitions and statutes |
| State court websites | Official forms, instructions, filing rules |
| [Docassemble](https://docassemble.org/) | Open-source document automation platform |

## Key Papers

- Sandefur (2020) — Access to justice: the role of technology
- Legal Services Corporation (2023) — The Justice Gap
- American Bar Association (2022) — Pro se litigation in family court
- National Center for State Courts — Self-represented litigant best practices

## Open Source Adjacencies

- [CourtListener](https://github.com/freelawproject/courtlistener) — Legal opinion + docket database
- [RECAP](https://github.com/freelawproject/recap) — PACER document archive
- [Docassemble](https://github.com/jhpyle/docassemble) — Document automation engine
- [A2J Author](https://www.a2jauthor.org/) — Guided court form interviews (proprietary)
- [CARDS (Court Automated Response Document System)](https://github.com/SuffolkLITLab) — Suffolk LIT Lab tools

## Success Criteria

- Complete a court-ready custody petition from a 5-minute natural language interview
- Capture 100% of filing deadlines correctly for the target state's family court
- Reduce form errors to <5% (vs. baseline where 40%+ of pro se filings are rejected)
- Generate hearing prep checklist that covers 90% of common judicial questions
- Legal aid org validation: 3 case studies completed with partner organizations

## Skills Needed

- **Full-stack development** (React + Python/Node.js)
- **Document automation** (Docassemble integration or PDF generation)
- **Legal domain knowledge** (family court procedure in at least one state)
- **LLM integration** (form assembly from natural language, plain-language explanations)
- **Privacy & security** (handling sensitive personal, medical, and financial data)
- **UI/UX for vulnerable users** (trauma-informed design, low-literacy accessibility)

## Risks

- **Unauthorized practice of law (UPL):** The #1 risk. Every output must be reviewed by legal partners. Clear disclaimers. Partner with LSC-funded organizations.
- **State/county fragmentation:** Every jurisdiction has different forms and rules. MVP must go deep in one state, not wide across many.
- **User vulnerability:** Family court involves trauma (divorce, abuse, custody disputes). Design must be sensitive, supportive, and avoid re-traumatization.
- **Data sensitivity:** Domestic violence cases, financial disclosures, and child custody battles produce extremely sensitive data. Privacy-first architecture is non-negotiable.
- **Evaluation difficulty:** "Success" in family court is hard to measure objectively. Define clear proxy metrics with partner orgs.
