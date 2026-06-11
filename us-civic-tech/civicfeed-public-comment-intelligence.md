---
track: us-civic-tech
status: published
---

# CivicFeed — Public Comment Intelligence Engine

> Transform the chaotic firehose of federal public comments into structured, actionable intelligence for agency staff and the public alike.

## The Problem

Federal agencies are legally required to consider every public comment submitted during rulemaking. The Administrative Procedure Act (APA) mandates this, but provides no mechanism for scalable analysis. During the 2017 net neutrality proceeding, the FCC received **22 million comments** — far beyond any human team's capacity to process meaningfully.

Today, agency staff manually work **3–6 person-weeks per docket**, reading through repetitive form letters, flagging spam, and attempting to surface novel arguments. With **7M+ documents** on Regulations.gov alone and thousands of open dockets at any time, agencies are drowning in participation they're legally obligated to honor — but practically cannot.

**AI can change this.** Large language models can extract substantive arguments from unstructured text, cluster them thematically, detect coordinated spam campaigns, and even map stakeholder positions — all at a fraction of the cost and time of manual review.

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| Manual staff review | 3–6 person-weeks per docket; doesn't scale past a few hundred comments |
| Form-letter counting | Misses substantive arguments buried in templated submissions |
| Basic keyword search | No thematic or argument-level understanding |
| DocketScope (closed-source) | $100K+/year licensing; inaccessible to small agencies, nonprofits, and the public |
| In-house ML experiments | One-off academic efforts; no production pipeline or maintained tooling |

## What to Build

An open-source comment intelligence platform that:

- **Extracts and clusters arguments** from unstructured public comments using LLMs (argument parsing, stance detection, thematic grouping)
- **Detects spam and coordinated campaigns** at scale (form-letter variants, bot detection)
- **Generates executive summaries** per docket — what arguments were raised, by whom, at what frequency
- **Maps stakeholders** to their stated positions (industry, advocacy, individual)
- **Assists response drafting** — given agency staff notes, suggest APA-compliant reply language
- **Exposes everything through a public dashboard** so anyone can inspect the analysis

**MVP (6–8 weeks solo):** A pipeline that ingests comments from Regulations.gov API v4, runs LLM-based argument extraction + clustering, and produces a summary report. Web UI for browsing results.

## Stakeholders

- **241M+ Americans** eligible to comment on federal rules
- **15,000+ federal regulatory analysts** across agencies
- **CDO Council** pilot programs on AI-assisted rulemaking
- **Advocacy organizations** tracking regulatory outcomes
- **Journalists** covering the regulatory state

## Data Sources

| Source | Description |
|---|---|
| [Regulations.gov API v4](https://open.gsa.gov/api/regulationsgov/) | 7M+ regulatory documents and public comments |
| [Federal Register API](https://www.federalregister.gov/developers/api/v1) | Official rulemaking notices and timelines |
| [CDO Council pilot data](https://www.cdo.gov/ai-pilot/) | Agency AI-assisted rulemaking experiments |
| [FCC Net Neutrality dataset](https://www.fcc.gov/ecfs/search/) | 22M+ net neutrality comments (classic scale test) |

## Key Papers

- Salas-Gironés et al. (2024) — LLM-assisted public comment analysis pipeline
- ScienceDirect (2026) — Large language models for regulatory comment summarization
- CDO Council (2023) — AI in rulemaking: opportunities and limitations
- APA Administrative Procedure Act (5 U.S.C. § 553) — legal framework

## Open Source Adjacencies

- [OpenRegulations.ai](https://openregulations.ai) — regulatory analysis tools
- [jmandel/regulations.gov-comment-browser](https://github.com/jmandel/regulations.gov-comment-browser) — comment exploration
- [regulations.gov API client libraries](https://open.gsa.gov/api/regulationsgov/) — Python/JS SDKs

## Success Criteria

- Process and summarize a docket of 10,000+ comments in under 2 hours
- Achieve >85% precision/recall on argument extraction vs. expert human annotation
- Detect coordinated campaigns with >90% accuracy compared to manual forensic review
- Produce a one-page executive summary per docket readable by a non-expert
- Deploy fully on open-source infrastructure (<$50/month in compute)

## Skills Needed

- **Python** (FastAPI, async processing)
- **LLM orchestration** (LangChain, LlamaIndex, or direct API workflows)
- **NLP basics** (embedding clustering, topic modeling)
- **React/TypeScript** for the dashboard UI
- **API integration** (Regulations.gov REST API)
- **Data pipeline engineering** (async queue processing, deduplication)

## Risks

- **Comment quality variance:** Many comments are spam, form letters, or off-topic — filtering is non-trivial
- **Ground truth for evaluation:** No standard benchmark for "good" argument extraction; need expert annotation
- **API rate limits:** Regulations.gov API has throttling; need responsible backoff/caching
- **Agency adoption:** Even great tools need champions inside agencies — build public-facing value first
- **LLM cost at scale:** Summarizing 100K+ comments is expensive; need smart sampling and caching strategies
