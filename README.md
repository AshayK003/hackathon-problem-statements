# 🏆 Hackathon Problem Statements

### Real-world problems that matter. Ready to build.

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Stars](https://img.shields.io/github/stars/AshayK003/hackathon-problem-statements?style=social)](https://github.com/AshayK003/hackathon-problem-statements)

---

## The Problem With Hackathons

Most hackathon problem statements are one of:
- **Underspecified** — "Build something with AI" (too vague to start)
- **Over-engineered** — Requires months of prior infrastructure
- **Fake** — Problems that don't exist outside a classroom

This repo fixes that. Every problem statement here is:
- **Real** — Grounded in actual data, stakeholders, and published research
- **Concrete** — Specific enough to start building in one sitting
- **Impactful** — Affects millions of people or billions of dollars
- **Scoped** — Clear MVP with estimated build time

---

## The Problem Sets

### 🌍 [Global South Impact](global-south-impact/)
**10 AI/ML projects** that solve invisible infrastructure problems in developing countries.
| # | Problem | Impact | MVP |
|---|---------|--------|-----|
| 01 | [Maternal Health Risk Stratification](global-south-impact/maternal-health-risk-stratification.md) | 287K lives/year | 6-8mo |
| 02 | [Public Procurement Fraud Detection](global-south-impact/public-procurement-fraud-detection.md) | $1.3-4T lost/year | 5-7mo |
| 03 | [Informal Waste Sector Platform](global-south-impact/informal-waste-sector-platform.md) | 15-20M workers | 6-8mo |
| 04 | [Post-Harvest Loss Intelligence](global-south-impact/post-harvest-loss-intelligence.md) | 30-40% food lost | 7-9mo |
| 05 | [Harmful Algal Bloom Early Warning](global-south-impact/harmful-algal-bloom-early-warning.md) | 60% US lakes at risk | 8-10mo |
| 06 | [Scientific Reproducibility Engine](global-south-impact/scientific-reproducibility-engine.md) | $28B/year wasted | 8-12mo |
| 07 | [Offline Crop Disease Diagnostics](global-south-impact/offline-crop-disease-diagnostics.md) | 500M+ farmers | 5-7mo |
| 08 | [Groundwater Depletion Forecasting](global-south-impact/groundwater-depletion-forecasting.md) | 2B+ people | 12-18mo |
| 09 | [School Resource Allocation Optimizer](global-south-impact/school-resource-allocation-optimizer.md) | 65M US students | 5-7mo |
| 10 | [Climate-Resilient Housing Design](global-south-impact/climate-resilient-housing-design.md) | 1B+ in slums | 10-14mo |

### 🇺🇸 [US Civic Tech](us-civic-tech/)
**10 consumer/civic projects** that navigate America's broken regulatory and social systems.
| # | Problem | Novelty | MVP |
|---|---------|---------|-----|
| 01 | [CivicFeed — Public Comment Intelligence](us-civic-tech/civicfeed-public-comment-intelligence.md) | 9/10 | 6-8w |
| 02 | [Workers Compass — Claim Navigator](us-civic-tech/workers-compass-claim-navigator.md) | 10/10 | 8-10w |
| 03 | [FOIAbot — Public Records Assistant](us-civic-tech/foiabot-public-records-assistant.md) | 9/10 | 6w |
| 04 | [DecodeMyBill — Medical Bill Intelligence](us-civic-tech/decodemybill-medical-bill-intelligence.md) | 7/10 | 10-12w |
| 05 | [ProSe Navigator — Family Court Assistant](us-civic-tech/prose-navigator-family-court-assistant.md) | 8/10 | 8-12w |
| 06 | [PredatoryGuard — Financial Analyzer](us-civic-tech/predatoryguard-financial-analyzer.md) | 9/10 | 6-8w |
| 07 | [UtilityCoach — Energy Assistance Navigator](us-civic-tech/utilitycoach-energy-assistance-navigator.md) | 8/10 | 6w |
| 08 | [HousingKey — Housing Program Navigator](us-civic-tech/housingkey-housing-program-navigator.md) | 8/10 | 10-12w |
| 09 | [InformedYou — Consent Simplifier](us-civic-tech/informedyou-consent-simplifier.md) | 7/10 | 6w |
| 10 | [SchoolEquityWatch — Funding Transparency](us-civic-tech/school-funding-transparency-analyzer.md) | 7/10 | 12-16w |

### ⚡ [Rapid Prototypes](rapid-prototype/)
**6 non-AI ideas** that can be built solo in 2-6 weeks — perfect for weekend hackathons.
| # | Problem | Type | Build Time |
|---|---------|------|-----------|
| 01 | [Village Grain Bank Manager](rapid-prototype/village-grain-bank-manager.md) | WhatsApp + CRUD | 2-3w |
| 02 | [Medicine Stock Visibility](rapid-prototype/medicine-stock-visibility.md) | WhatsApp + Inventory | 2-4w |
| 03 | [Infrastructure Defect Reporter](rapid-prototype/infrastructure-defect-reporter.md) | Maps + Workflow | 3-4w |
| 04 | [Procurement Data Quality Monitor](rapid-prototype/procurement-data-quality-monitor.md) | Data Engineering | 3-4w |
| 05 | [Informal Worker Skills Passport](rapid-prototype/informal-worker-skills-passport.md) | Offline Mobile | 4-6w |
| 06 | [School Resource Transparency Map](rapid-prototype/school-resource-transparency-map.md) | Maps + Offline Forms | 4-6w |

---

## How to Use This Repo

**For Hackathon Organizers:**
Pick problems appropriate for your event's duration and your participants' skill level. Each problem has a clear MVP scope. The `rapid-prototype/` set is ideal for 24-48h events.

**For Hackathon Participants:**
1. Browse the sets → pick a problem that matches your team's skills
2. Read the full problem statement → it has datasets, papers, and adjacent OSS
3. Build the MVP → each problem has clear success criteria
4. Contribute back → submit a PR with your implementation notes

**For Contributors:**
See [CONTRIBUTING.md](CONTRIBUTING.md) — we accept new problem statements via the template at `_PROBLEM_TEMPLATE.md`, improvements to existing statements, and implementation notes from teams who built a solution.

---

## What Makes These Different

| Feature | This Repo | Typical Hackathon Problems |
|---------|-----------|---------------------------|
| Real data sources | ✅ Datasets + APIs linked | ❌ Vague |
| Academic grounding | ✅ Papers cited per problem | ❌ None |
| Stakeholder analysis | ✅ Who this affects + scale | ❌ None |
| MVP scope | ✅ Weeks/months estimated | ❌ No scope |
| Open-source adjacencies | ✅ What already exists | ❌ No landscape |
| Tech feasibility | ✅ AI vs non-AI labeled | ❌ No guidance |

---

## Selection Criteria

Every problem in this repo passed all of these filters:

- **Not a chatbot wrapper, generic RAG, CRUD dashboard, note-taking tool, meeting summarizer, productivity app, AI code assistant, or social network clone**
- Strong societal or economic impact
- Existing datasets and/or research literature
- AI/tech genuinely adds value (not a gimmick)
- No saturated open-source solution already dominates
- Technically feasible for a motivated team

---

## Repo Structure

```
problem-statements/
├── global-south-impact/      # AI/ML for the developing world
│   ├── README.md             # Track overview + skill requirements
│   └── 10 problem statements
├── us-civic-tech/            # Consumer/civic for the US
│   ├── README.md
│   └── 10 problem statements
├── rapid-prototype/          # Non-AI ideas for fast shipping
│   ├── README.md
│   └── 6 problem statements
├── _PROBLEM_TEMPLATE.md      # Template for new contributions
├── INDEX.md                  # Searchable master index
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── LICENSE
```

---

## Stats

- **26** problem statements (and growing)
- **3** tracks (Global South AI, US Civic Tech, Rapid Prototypes)
- **20** AI/ML problems + **6** pure engineering problems
- **150+** research papers cited
- **100+** datasets and APIs linked
- **50+** open-source adjacencies mapped

---

## License

MIT — use, fork, remix, build. If you start a company based on one of these, we'd love to hear about it.

---

## Inspiration & Research

These problem statements are the result of systematic landscape analysis across 30+ domains, 70+ papers, and 50+ candidate problems by [AshayK003](https://github.com/AshayK003). Research conducted June 2026.
