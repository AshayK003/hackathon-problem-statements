# 🏆 Problem Statements Worth Building

### Real-world problems for hackathons, college projects, and developer portfolios. Ready to build. Open for contributions.

This is the largest curated collection of **real-world problem statements** (46 problems across 5 tracks) — built for hackathons, college major/minor projects, capstones, and developer portfolios. Every problem is grounded in actual data, peer-reviewed research, and serves real stakeholders — not hypotheticals.

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![GitHub Repo Stars](https://img.shields.io/badge/github-stars-social?style=social&label=Star)](https://github.com/AshayK003/hackathon-problem-statements)
[![Problems](https://img.shields.io/badge/problems-46-8A2BE2)](INDEX.md)
[![Research Papers Cited](https://img.shields.io/badge/papers-200%2B-blue)](INDEX.md)
[![Datasets Linked](https://img.shields.io/badge/datasets-100%2B-success)](INDEX.md)

---

**Stop building chatbots and CRUD dashboards.** Build something that actually matters.

## The 5 Tracks

| Track | Format | Build Time | Best For |
|-------|--------|-----------|----------|
| 🌍 [Global South Impact](global-south-impact/) | **10 AI/ML** problems | 5–18 months | Teams with ML + domain expertise |
| 🇺🇸 [US Civic Tech](us-civic-tech/) | **10 LLM/data** problems | 6–16 weeks | Teams building for consumer impact |
| 🇮🇳 [India Impact](india-impact/) | **5 AI/agent** problems | 8–16 weeks | Solo devs with DPI API experience |
| 🧠 [Frontier AI Platforms](frontier-platforms/) | **10 AI-governance/health** problems | 2–6 months | Solo devs tackling systemic risks |
| ⚡ [Rapid Prototypes](rapid-prototype/) | **11 engineering** problems | 2–6 weeks | Solo devs, weekend hackathons |

---

## The Problem With Hackathons

**Most hackathon prompts fall into three failure modes:**

| Failure Mode | Example | Why It Fails |
|-------------|---------|-------------|
| 🫗 **Underspecified** | *"Build something with AI for healthcare"* | Too vague to start building. Teams spend 50% of the event deciding what to do. |
| 🏗️ **Over-engineered** | *"Build a federated learning platform for genomics"* | Requires months of prior infrastructure. Unbuildable in a weekend. |
| 🎭 **Fake** | *"Airbnb for pets"* | Doesn't solve a real problem. Judges can smell it. Won't survive outside the classroom. |

**This repo fixes all three.** Every problem statement here is:

- ✅ **Real** — Grounded in actual data sources, government datasets, published research, and quantified stakeholders
- ✅ **Concrete** — Specific enough to start building in one sitting. Datasets linked. Papers cited. Adjacent OSS mapped.
- ✅ **Impactful** — Affects millions of people or billions of dollars. Every problem has a built-in "why this matters" case.
- ✅ **Scoped** — Clear MVP timeline with success criteria. You know *exactly* what "done" looks like.
- ✅ **Feasible** — Build-time estimated by complexity. AI vs non-AI labeled. Solo-friendly options available.

---

## Who This Is For

| Audience | Why This Repo Exists For You |
|----------|------------------------------|
| **Hackathon participants** | Stop wasting 4 hours debating ideas. Pick a battle-tested problem from the list and start building in 15 minutes. |
| **Hackathon organizers** | Ditch the vague theme. Drop real problem statements that produce working, fundable prototypes — not another todo app. |
| **College students (minor projects)** | Need a 1-semester project that actually works? Every Rapid Prototype and most US Civic Tech problems are scoped to build in 6–16 weeks with clear success criteria. No fluff. |
| **College students (major projects / capstone)** | Looking for something with enough depth for a year-long thesis? Global South Impact and Frontier AI Platform problems have research citations, data sources, and evaluation frameworks built in. |
| **Portfolio builders** | Want a GitHub that gets you hired? These problems produce demonstrable, real-world projects — not another CRUD dashboard. Recruiters pay attention when you can say "I built a fraud detection system used by X people." |
| **University clubs & CS departments** | Give students problems that connect coursework to real-world impact. Every problem links to papers and datasets with clear scope for a semester project. |
| **Open-source contributors** | Find a problem you care about and start building. The repo is designed for low-friction contribution. |
| **Indie developers & founders** | Each problem statement is a potential startup idea with identified stakeholders, market gaps, and monetization paths. |
| **NGOs & government agencies** | Submit problems from the field. The `_PROBLEM_TEMPLATE.md` makes this a 15-minute contribution. |

---

## 🎓 For College Students & Portfolio Builders

This repo was built for you as much as for hackathon teams. Here's how to pick the right problem for your context.

### By Academic Scope

| Project Type | Timeframe | Recommended Track | Why |
|-------------|-----------|------------------|-----|
| **Minor Project** (1 semester) | 8–16 weeks | [Rapid Prototypes](rapid-prototype/) or [US Civic Tech](us-civic-tech/) | Scoped for solo development. Clear MVP. No research phase needed. |
| **Major Project** (2 semesters) | 16–32 weeks | [India Impact](india-impact/) or [Frontier AI Platforms](frontier-platforms/) | Real API integration, multiple components. Enough depth for a proper evaluation. |
| **Capstone / Thesis** (1 academic year) | 6–18 months | [Global South Impact](global-south-impact/) or [Frontier AI Platforms](frontier-platforms/) | Research-grounded. Papers to cite. Datasets to analyze. Genuine open-endedness. |
| **Portfolio project** | As long as it takes | Any track — pick what excites you | Pick something you can demo end-to-end. A solved problem with real data beats a half-baked complex idea. |

### Choosing the Right Problem — A Framework

Not every problem fits every student. Use this filter:

```
Academic level → Available time → Skills you want to learn → Domain you care about → Pick 3 problems → Read all 3 → Build the one that excites you most
```

**Minor project checklist:**
- [ ] Can I build the MVP in <10 weeks?
- [ ] Do I already know 70% of the tech stack?
- [ ] Is there a working demo I can show in 2 minutes?
- [ ] Does it produce something someone could actually use?

**Major project / thesis checklist:**
- [ ] Are there enough research papers to build a literature review? (→ Global South, Frontier AI)
- [ ] Is there real data I can access? (→ all problems link datasets)
- [ ] Can I frame an evaluation (A/B test, benchmark, user study)?
- [ ] Will I still be excited about this in month 5?

### Portfolio Strategy

A GitHub portfolio with one of these problems says more than five tutorial projects. Here's why:

| Instead of building… | Build one of these… | Why it wins |
|---------------------|---------------------|-------------|
| A weather dashboard (tutorial clone) | [CivicFeed](us-civic-tech/civicfeed-public-comment-intelligence.md) — Public Comment AI | Production NLP + government API. Real stakeholder. |
| A Twitter clone (everyone's done it) | [FOIAbot](us-civic-tech/foiabot-public-records-assistant.md) — FOIA Assistant | Legal tech. Document intelligence. Zero competitors. |
| A CRUD todo app | [Village Grain Bank](rapid-prototype/village-grain-bank-manager.md) — WhatsApp Banking for Farmers | Offline-first architecture. Real users. Actual impact. |
| A chatbot wrapper | [DecodeMyBill](us-civic-tech/decodemybill-medical-bill-intelligence.md) — Medical Bill Parser | Domain expertise signal. Healthcare + OCR + LLMs. |
| An e-commerce site | [Vyavastha](india-impact/vyavastha-msme-compliance-copilot.md) — MSME Compliance Copilot | B2B SaaS potential. Multiple API integrations. |

**Pro tip:** Contribute your implementation notes back as a PR. A repo that shows both "built this" and "documented how" is the kind of candidate teams fight over.

---

## The Problem Sets

### 🌍 [Global South Impact](global-south-impact/) — AI/ML for the Developing World

**10 problems** that solve invisible infrastructure challenges in low-resource settings — where commercial SaaS doesn't compete because customers can't pay market rates.

| # | Problem | Impact | Build Time | Tags |
|---|---------|--------|-----------|------|
| 01 | [Maternal Health Risk Stratification](global-south-impact/maternal-health-risk-stratification.md) | 287K maternal deaths/year | 6–8 mo | `health` `ML` `offline` |
| 02 | [Public Procurement Fraud Detection](global-south-impact/public-procurement-fraud-detection.md) | $1.3–4T lost/year | 5–7 mo | `governance` `GNN` |
| 03 | [Informal Waste Sector Platform](global-south-impact/informal-waste-sector-platform.md) | 15–20M informal workers | 6–8 mo | `environment` `CV` |
| 04 | [Post-Harvest Loss Intelligence](global-south-impact/post-harvest-loss-intelligence.md) | 30–40% food lost | 7–9 mo | `agriculture` `IoT` |
| 05 | [Harmful Algal Bloom Early Warning](global-south-impact/harmful-algal-bloom-early-warning.md) | 60% US lakes at risk | 8–10 mo | `water` `remote-sensing` |
| 06 | [Scientific Reproducibility Engine](global-south-impact/scientific-reproducibility-engine.md) | $28B/year wasted | 8–12 mo | `science` `LLM` |
| 07 | [Offline Crop Disease Diagnostics](global-south-impact/offline-crop-disease-diagnostics.md) | 500M+ farmers | 5–7 mo | `agriculture` `TFLite` `offline` |
| 08 | [Groundwater Depletion Forecasting](global-south-impact/groundwater-depletion-forecasting.md) | 2B+ people | 12–18 mo | `water` `climate` `satellite` |
| 09 | [School Resource Allocation Optimizer](global-south-impact/school-resource-allocation-optimizer.md) | 65M US students | 5–7 mo | `education` `optimization` |
| 10 | [Climate-Resilient Housing Design](global-south-impact/climate-resilient-housing-design.md) | 1B+ in slums | 10–14 mo | `housing` `climate` `gen-AI` |

**🏁 Fastest MVP:** [Offline Crop Disease Diagnostics](global-south-impact/offline-crop-disease-diagnostics.md) (TFLite on-device, 5–7 months, solo-buildable)

---

### 🇺🇸 [US Civic Tech](us-civic-tech/) — Consumer Advocates for Broken Systems

**10 problems** that navigate America's most opaque consumer-facing systems — medical billing, workers' comp, family court, FOIA, public comments, predatory lending, housing assistance, and school funding. Every one affects millions, has public data available, and currently has **no open-source consumer advocate**.

| # | Problem | Novelty | MVP Time | Why It Exists |
|---|---------|---------|----------|---------------|
| 01 | [CivicFeed — Public Comment Intelligence](us-civic-tech/civicfeed-public-comment-intelligence.md) | **9/10** | 6–8 wks | Agencies spend 3–6 person-weeks per docket reading comments |
| 02 | [Workers Compass — Claim Navigator](us-civic-tech/workers-compass-claim-navigator.md) | **10/10** 🏆 | 8–10 wks | $50B industry, zero consumer competitors |
| 03 | [FOIAbot — Public Records Assistant](us-civic-tech/foiabot-public-records-assistant.md) | **9/10** | 6 wks | Journalists spend months per FOIA request |
| 04 | [DecodeMyBill — Medical Bill Intelligence](us-civic-tech/decodemybill-medical-bill-intelligence.md) | 7/10 | 10–12 wks | 80% of medical bills have errors |
| 05 | [ProSe Navigator — Family Court Assistant](us-civic-tech/prose-navigator-family-court-assistant.md) | **8/10** | 8–12 wks | 70–80% self-represented in family court |
| 06 | [PredatoryGuard — Financial Analyzer](us-civic-tech/predatoryguard-financial-analyzer.md) | **9/10** | 6–8 wks | $10B+ in scam losses/year |
| 07 | [UtilityCoach — Energy Assistance Navigator](us-civic-tech/utilitycoach-energy-assistance-navigator.md) | **8/10** | 6 wks | 80% of eligible households never apply for LIHEAP |
| 08 | [HousingKey — Housing Program Navigator](us-civic-tech/housingkey-housing-program-navigator.md) | **8/10** | 10–12 wks | 20M+ households with worst-case housing needs |
| 09 | [InformedYou — Consent Simplifier](us-civic-tech/informedyou-consent-simplifier.md) | 7/10 | 6 wks | Consent forms written at college level; avg US adult reads at 8th grade |
| 10 | [SchoolEquityWatch — Funding Transparency](us-civic-tech/school-funding-transparency-analyzer.md) | 7/10 | 12–16 wks | High-poverty districts receive 16% less funding — data is buried |

**🏁 Most defensible:** [Workers Compass](us-civic-tech/workers-compass-claim-navigator.md) ($50B workers' comp industry, **zero** consumer-facing competitors)

---

### 🇮🇳 [India Impact](india-impact/) — AI on India's DPI Layer

**5 AI problems** targeting India's Digital Public Infrastructure (DPI). Unlike US civic tech (fragmented) or generic Global South problems (pre-DPI), India's plumbing is built — APIs exist for land records, court cases, agricultural prices, and 740+ government schemes. But the **intelligent application layer** is missing.

| # | Problem | Type | MVP | Startup Potential |
|---|---------|------|-----|------------------|
| 01 | [Kisaan Marg — Mandi Price Intelligence](india-impact/kisaan-marg-mandi-price-intelligence.md) | Agmarknet API + LLM agent + WhatsApp | **10–12 wks** | ₹10,000 Cr/yr leakage |
| 02 | [Vyavastha — MSME Compliance Copilot](india-impact/vyavastha-msme-compliance-copilot.md) | Regtech agent + API orchestration | **12–16 wks** | 6.45Cr customers |
| 03 | [JalGuru — Water Quality Intelligence](india-impact/jalguru-water-quality-intelligence.md) | Geospatial ML + alerts | **8–10 wks** | Public health mission |
| 04 | [Nyaya Sahayak — Court Case Navigator](india-impact/nyaya-sahayak-court-case-navigator.md) | eCourt API + LLM + WhatsApp | **8–12 wks** | 52M pending cases |
| 05 | [Sarthak — Government Scheme Agent](india-impact/sarthak-government-scheme-agent.md) | Eligibility engine + DigiLocker | **8–10 wks** | ₹7.67L Cr in schemes |

**🏁 Best startup bet:** [Vyavastha](india-impact/vyavastha-msme-compliance-copilot.md) (MSMEs pay ₹13–17L/yr for compliance — will pay for a cheaper alternative)

---

### 🧠 [Frontier AI Platforms](frontier-platforms/) — AI Governance, Health & Systemic Risk

**10 problems** at the frontier of AI application — algorithmic auditing, antimicrobial resistance, clinical trial equity, dementia care, wildfire resilience, and more. These sit where AI capability meets systemic risk. Each problem has a clear regulatory or scientific framework behind it.

| # | Problem | Domain | Build Time | Stack |
|---|---------|--------|-----------|-------|
| 01 | [Algorithmic Bias Auditing Platform](frontier-platforms/algorithmic-bias-auditing-platform.md) | AI governance | 2–3 mo | AIF360, FairLearn, SHAP |
| 02 | [Youth Mental Health Crisis Triage](frontier-platforms/youth-mental-health-crisis-triage.md) | Mental health | 3–4 mo | NLP, risk models |
| 03 | [Clinical Trial Matching & Patient Equity](frontier-platforms/clinical-trial-matching-equity.md) | Health equity | 3–4 mo | LLM, OMOP CDM, FHIR |
| 04 | [Homelessness Prevention Early Warning](frontier-platforms/homelessness-prevention-early-warning.md) | Social services | 4–5 mo | ML, court data |
| 05 | [AMR Surveillance & Prescribing Support](frontier-platforms/amr-surveillance-prescribing-support.md) | Global health | 4–6 mo | WHO data, CLSI, FHIR |
| 06 | [Dementia Caregiver Decision Support](frontier-platforms/dementia-caregiver-decision-support.md) | Aging | 3–4 mo | RAG, clinical guidelines |
| 07 | [Food Waste Surplus Redistribution](frontier-platforms/food-waste-surplus-redistribution.md) | Climate | 3–4 mo | OR, supply-chain |
| 08 | [Wildfire Risk & Community Preparedness](frontier-platforms/wildfire-risk-preparedness.md) | Climate | 3–5 mo | Geospatial ML, satellite |
| 09 | [Perinatal Mental Health Platform](frontier-platforms/perinatal-mental-health-platform.md) | Maternal health | 2–3 mo | NLP, screening tools |
| 10 | [SMB Cybersecurity Compliance](frontier-platforms/smb-cybersecurity-compliance.md) | Cybersecurity | 2–3 mo | NIST, CMMC, LLM |

**🏁 Fastest build:** [Algorithmic Bias Auditing](frontier-platforms/algorithmic-bias-auditing-platform.md) or [Perinatal Mental Health](frontier-platforms/perinatal-mental-health-platform.md) (2–3 months with existing frameworks)

---

### ⚡ [Rapid Prototypes](rapid-prototype/) — Build for Impact in a Weekend

**11 non-AI ideas** scoped for solo developers and weekend hackathons. No AI, no computer vision — just solid engineering that changes lives. Pure CRUD, maps, WhatsApp bots, and data pipelines.

| # | Problem | Stack | Build Time | Learning Curve |
|---|---------|-------|-----------|---------------|
| 01 | [Village Grain Bank Manager](rapid-prototype/village-grain-bank-manager.md) | Twilio + CRUD + Inventory | **2–3 wks** | ★☆☆☆☆ |
| 02 | [Medicine Stock Visibility](rapid-prototype/medicine-stock-visibility.md) | WhatsApp/SMS + Inventory | **2–4 wks** | ★☆☆☆☆ |
| 03 | [Infrastructure Defect Reporter](rapid-prototype/infrastructure-defect-reporter.md) | Maps + Escalation Workflow | **3–4 wks** | ★★☆☆☆ |
| 04 | [Procurement Data Quality Monitor](rapid-prototype/procurement-data-quality-monitor.md) | Data Pipeline + Dashboard | **3–4 wks** | ★★☆☆☆ |
| 05 | [Informal Worker Skills Passport](rapid-prototype/informal-worker-skills-passport.md) | Offline Mobile + QR | **4–6 wks** | ★★★☆☆ |
| 06 | [School Resource Transparency Map](rapid-prototype/school-resource-transparency-map.md) | Offline Forms + Maps | **4–6 wks** | ★★★☆☆ |
| **07** | [Annapurna — PDS Tracker](rapid-prototype/annapurna-pds-tracker.md) | WhatsApp + Maps + API | **4–6 wks** | ★★★☆☆ |
| **08** | [RathLink — Waste Worker Platform](rapid-prototype/rathlink-waste-worker-platform.md) | QR + Offline Mobile | **4–6 wks** | ★★★☆☆ |
| **09** | [BhuLekh — Land Records App](rapid-prototype/bhulekh-land-records-app.md) | API Search + Maps | **3–4 wks** | ★★☆☆☆ |
| **10** | [Setu — Government Form Assistant](rapid-prototype/setu-government-form-assistant.md) | Form Engine + DigiLocker | **3–4 wks** | ★★☆☆☆ |
| **11** | [JalSathi — Water Testing Network](rapid-prototype/jalsathi-water-testing-network.md) | Maps + SMS + Crowdsource | **4–6 wks** | ★★★☆☆ |

**🏁 24-hour hackathon pick:** [Village Grain Bank Manager](rapid-prototype/village-grain-bank-manager.md) or [Medicine Stock Visibility](rapid-prototype/medicine-stock-visibility.md)

---

## How to Use This Repo

### 🎯 For Hackathon Teams (5-minute start)

1. **How much time do you have?**
   - **24–48 hours** → Go straight to [Rapid Prototypes](rapid-prototype/)
   - **1–4 weeks** → Pick a [US Civic Tech](us-civic-tech/) problem
   - **1–6 months** → Your pick — all tracks open
2. **What's your team's skill stack?**
   - Computer vision → [Global South Impact #3](global-south-impact/informal-waste-sector-platform.md), [#7](global-south-impact/offline-crop-disease-diagnostics.md)
   - LLMs / NLP → [US Civic Tech #1–#10](us-civic-tech/) (all leverage LLMs differently)
   - Full-stack, no ML → [Rapid Prototypes](rapid-prototype/) (pure engineering impact)
3. **Read the problem statement** → datasets linked, papers cited, OSS to build on
4. **Ship the MVP** → every problem has clear success criteria
5. **Contribute back** → PR your implementation notes

### 🏫 For Organizers & Educators

Pick problems proportional to your event or semester duration:

| Event Length | Recommended Track | Rationale |
|-------------|------------------|-----------|
| 24–48 hours | **Rapid Prototypes** | Fully buildable solo over a weekend |
| 1 week | **US Civic Tech** (select 3–5) | LLM-powered, fast iteration |
| 1–3 months | **Global South Impact** | Real ML, CV, or systems project |
| Semester-long | **Any + mentorship** | Research-grade implementation |

### 🎓 For College Students

**Quick pick by your situation:**

- **Minor project this semester** → [Rapid Prototypes](rapid-prototype/) — 2–6 week builds, no ML required, solo-scoped. Village Grain Bank or Medicine Stock Visibility are perfect starter projects.
- **Major project (year-long)** → [US Civic Tech](us-civic-tech/) or [India Impact](india-impact/) — 8–16 week scope leaves room for literature review, implementation, and evaluation. Workers Compass or Vyavastha have startup-level depth.
- **Capstone / thesis** → [Global South Impact](global-south-impact/) or [Frontier AI Platforms](frontier-platforms/) — 5–18 month scope, research-grounded, publishable results. Pick one with datasets you can access and papers you can cite.
- **Portfolio piece to get hired** → Any track, but prioritize problems that let you show: architecture decisions, testing strategy, CI/CD, and a live or recorded demo.

**Academic workflow:**

```bash
1. Browse by domain → INDEX.md lists all problems by domain, skill, and geography
2. Read 3 problem statements → find one that excites you
3. Check data availability → every problem links datasets upfront
4. Draft a project proposal → the problem statement IS your proposal (problem, data, methods, success criteria)
5. Build the MVP → success criteria tell you exactly what "done" looks like
6. Write the report → problem statement gives you the introduction and related work
7. Submit feedback → PR your experience to help the next student
```

### 🤝 For Contributors

See [CONTRIBUTING.md](CONTRIBUTING.md). Three ways to contribute:

1. **Submit a new problem** — Use `_PROBLEM_TEMPLATE.md` (15-minute task)
2. **Improve an existing one** — Add datasets, fix errors, add adjacent OSS
3. **Implementation notes** — Built a solution? Share architecture, pitfalls, and lessons learned

---

## What Makes This Different From Every Other Hackathon Problem List

| Feature | This Repo | Typical Hackathon Problems |
|---------|-----------|---------------------------|
| **Real data sources** | ✅ Every problem has linked datasets and API endpoints | ❌ Vague or absent |
| **Academic grounding** | ✅ 200+ peer-reviewed papers cited across 46 problems | ❌ None |
| **Stakeholder analysis** | ✅ Quantified: who's affected, at what scale, with sources | ❌ None |
| **MVP scope** | ✅ Build time estimated in weeks or months per problem | ❌ "Build something cool" |
| **Open-source adjacencies** | ✅ 80+ existing OSS projects mapped per track | ❌ No landscape awareness |
| **AI vs non-AI labeled** | ✅ Clear labeling so teams pick by available skills | ❌ No guidance |
| **Novelty scoring** | ✅ Every US Civic Tech problem scored 7–10/10 | ❌ None |
| **Monetization paths** | ✅ B2G / B2B / open-core models for each prototype | ❌ None |
| **Failure mode analysis** | ✅ "Why existing solutions fail" for every problem | ❌ None |
| **Success criteria** | ✅ Checklist-style "what done looks like" per problem | ❌ None |

---

## Quick Navigation by Build Time

| Build Time | What You Can Build |
|-----------|-------------------|
| **2–3 weeks** | Village Grain Bank, Medicine Stock Visibility |
| **3–4 weeks** | Infrastructure Defect Reporter, Procurement Data Quality Monitor, BhuLekh, Setu |
| **4–6 weeks** | Informal Worker Skills Passport, School Resource Transparency Map, Annapurna, RathLink, JalSathi |
| **6–8 weeks** | CivicFeed, FOIAbot, PredatoryGuard, UtilityCoach, InformedYou |
| **8–12 weeks** | Workers Compass, DecodeMyBill, ProSe Navigator, HousingKey, Kisaan Marg, JalGuru, Nyaya Sahayak, Sarthak |
| **12–16 weeks** | SchoolEquityWatch, Climate-Resilient Housing, Vyavastha |
| **5–7 months** | Procurement Fraud, Offline Crop Disease, School Resource Optimizer |
| **6–8 months** | Maternal Health, Informal Waste, Post-Harvest Loss |
| **8–10 months** | Harmful Algal Bloom Early Warning |
| **8–12 months** | Scientific Reproducibility Engine |
| **12–18 months** | Groundwater Depletion Forecasting |

---

## Selection Criteria

Every problem in this repo had to pass **all** of these filters:

- ❌ **Not** a chatbot wrapper, generic RAG, CRUD dashboard, note-taking tool, meeting summarizer, productivity app, AI code assistant, or social network clone
- ✅ Strong societal or economic impact (millions of people or billions of dollars)
- ✅ Existing datasets **and/or** published research literature to ground the problem
- ✅ AI/tech genuinely adds value — not a gimmick
- ✅ No saturated open-source solution already dominates the space
- ✅ Technically feasible for a motivated team (any skill level)

---

## Repo Structure

```
hackathon-problem-statements/
├── global-south-impact/       # 10 AI/ML problems for the developing world
│   ├── README.md              # Track overview with quick-start guides
│   └── 10 problem statements  # Each: problem, data, papers, OSS, criteria
├── india-impact/              # 5 AI problems on India's DPI layer
│   ├── README.md              # Track overview with quick-start guides
│   └── 5 problem statements
├── us-civic-tech/             # 10 consumer/civic problems for the US
│   ├── README.md              # Track overview with novelty scores
│   └── 10 problem statements
├── rapid-prototype/           # 11 engineering problems, 2–6 weeks each
│   ├── README.md              # Track overview with week-by-week timelines
│   └── 11 problem statements
├── frontier-platforms/        # 10 AI-governance/health problems
│   └── 10 problem statements  # Each: problem, regulatory framework, data
├── _PROBLEM_TEMPLATE.md       # Template for submitting new problems
├── INDEX.md                   # Master index — filterable by time, skill, domain
├── CONTRIBUTING.md            # How to contribute
├── CODE_OF_CONDUCT.md         # Community standards
└── LICENSE                    # MIT — free to use, fork, build
```

---

## Stats

| Metric | Count |
|--------|-------|
| Total problem statements | **46** (and growing) |
| Tracks | **5** (Global South AI, US Civic Tech, India Impact, Frontier AI Platforms, Rapid Prototypes) |
| AI/ML problems | **35** |
| Pure engineering problems | **11** |
| Research papers cited | **200+** |
| Datasets and APIs linked | **100+** |
| Open-source adjacencies mapped | **80+** |
| Domains covered | **20+** (health, agriculture, governance, education, water, housing, energy, labor, finance, science, legal, climate, transparency, infrastructure, environment, cybersecurity, mental health, food security, AI governance, clinical research) |
| Shortest build time | **2 weeks** |
| Longest build time | **18 months** |

---

## Frequently Asked Questions

**Q: Are these actually buildable by a hackathon team?**  
Yes. Every problem has a clear MVP scope. The [Rapid Prototypes](rapid-prototype/) are built specifically for 24–48 hour events. The [US Civic Tech](us-civic-tech/) problems are designed for LLM-powered fast iteration over weeks. The [Global South Impact](global-south-impact/) problems require more time but have the largest potential impact.

**Q: I don't know ML. Can I still contribute?**  
Absolutely. The entire [Rapid Prototypes](rapid-prototype/) track requires zero ML — just solid full-stack engineering. Plus, many [US Civic Tech](us-civic-tech/) problems can be tackled by integrating LLM APIs (you consume the model, you don't train one).

**Q: Where do the problems come from?**  
Systematic landscape analysis across 30+ domains, 70+ papers, and 50+ candidate problems by [AshayK003](https://github.com/AshayK003). Each problem was validated against real-world data sources, existing research, and stakeholder analysis.

**Q: Can I submit a new problem?**  
Yes — and we want you to. Use `_PROBLEM_TEMPLATE.md` and open a PR. See [CONTRIBUTING.md](CONTRIBUTING.md). We especially welcome problems from NGOs, government agencies, and domain experts.

**Q: Can I fork this and use it for my own hackathon event?**  
Yes — it's MIT licensed. Use it, remix it, customize it for your event. We'd appreciate a shoutout but legally you don't need one.

**Q: Has anyone built a solution for any of these?**  
Not yet — that's the point. These are open problems waiting for a team to step up. If you build one, submit implementation notes via PR.

**Q: I'm a college student — can I use this for my minor/major project?**  
That's exactly what the [🎓 For College Students](#-for-college-students--portfolio-builders) section is for. Every problem has clear scope, success criteria, datasets, and research citations — so you can spend your time building, not defining. The problem statement doubles as your project proposal introduction and related work section.

**Q: Will putting one of these in my portfolio help me get a job?**  
A real-world project with actual data, a working demo, and documented architecture beats five tutorial clones every time. Recruiters notice when you can say "I built a tool that addresses an X-billion-dollar problem." The [Portfolio Strategy](#portfolio-strategy) section has specific recommendations.

---

## License

**MIT** — use, fork, remix, build a company on it. If you start a business based on one of these, [let us know](https://github.com/AshayK003) — we'd love to feature it.

---

## Developer Support

If these problem statements help you build something meaningful — or you just want to say thanks — consider supporting the developer:

<a href="https://chai4.me/ashaykushwaha003" target="_blank" title="Support on Chai4Me" style="display:inline-flex;flex-direction:column;align-items:center;justify-content:center;background:#ffffff;padding:8px 32px;border-radius:16px;text-decoration:none;border:1px solid #e5e7eb;box-shadow:0 4px 6px -1px rgba(0,0,0,0.05), 0 2px 4px -2px rgba(0,0,0,0.05);transition:transform 0.2s;"><img src="https://chai4.me/icons/wordmark.png" alt="Chai4Me" style="height:32px;object-fit:contain;margin-bottom:4px;"/><span style="color:#6b7280;font-family:sans-serif;font-size:14px;font-weight:600;">@ashaykushwaha003</span></a>

---

<div align="center">

**⭐ [Star this repo](https://github.com/AshayK003/hackathon-problem-statements) — help the next team find a problem worth building.**

[View Full Index](INDEX.md) · [Submit a Problem](_PROBLEM_TEMPLATE.md) · [Contribution Guide](CONTRIBUTING.md)

</div>
