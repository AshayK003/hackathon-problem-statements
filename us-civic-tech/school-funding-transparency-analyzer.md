---
track: us-civic-tech
status: published
---

# SchoolEquityWatch — Public School Funding Transparency Analyzer

> Public school funding is the most opaque system in American governance. High-poverty districts receive 16% less. ESSA promised transparency — but the data is still buried in spreadsheets. Expose the gaps.

## The Problem

In the United States, school funding is not just inequitable — it's intentionally opaque. **Property-tax-based funding** means that wealthy districts naturally raise more money than poor ones. State funding formulas attempt to close the gap, but they're so complex that even school board members and state legislators don't fully understand them.

The result: **high-poverty school districts receive 16% less funding per student** than low-poverty districts. In some states, the gap is **30% or more**.

The Every Student Succeeds Act (ESSA) of 2015 required, for the first time, that states report **per-pupil spending at the individual school level**. This was a historic transparency breakthrough — but the data is buried in downloadable spreadsheets, formatted differently by every state, and never analyzed for equity. **13,000+ school districts** and nearly **100,000 schools** report data in ways that make comparison nearly impossible.

Parents, school board members, advocates, and even policymakers have no easy way to answer basic questions: Does my district fund schools equitably? How does my child's school compare to others in the district? What would happen if we changed the funding formula?

## Why Existing Solutions Fail

| Approach | Limitation |
|---|---|
| NCES Data Tools | Query-based; technical interface; no analysis or visualization |
| State education department websites | Raw spreadsheets; 50 different formats; no equity analysis |
| School Finance Indicators Database | Academic research tool; not for parent/advocate use |
| EdBuild / EdTrust reports | Static one-time studies; no interactive, queryable tool |
| School board meetings | Subjective anecdote; no data to support equity arguments |
| **No interactive funding equity tool exists** | Zero products let users explore, compare, and simulate funding |

## What to Build

An interactive school funding transparency and equity analyzer that:

- **Explains funding formulas in plain language** — how your state distributes money, what factors matter, who wins and loses
- **Conducts equity analysis at multiple levels** — within-district (school-to-school), across-district (statewide), and by student demographics
- **Provides what-if simulation** — what happens to your school's funding if the state formula changes, if property tax rates shift, if student counts change
- **Enables school-level comparison** — side-by-side per-pupil spending for any schools in any district
- **Analyzes policy impact** — how proposed legislation would shift funding between districts
- **Generates advocacy briefs** — one-page PDF summaries designed for school board meetings, legislative testimony, and parent organizing
- **Tracks equity trends over time** — is your state's funding gap growing or shrinking?

**MVP (12–16 weeks solo):** ESSA school-level spending visualization + within-district equity gap analysis for one state. Single-state what-if simulator.

## Stakeholders

- **50M+ K-12 students** and their families
- **13,000+ school districts** and their administrators
- **100,000+ school board members** making funding decisions
- **State legislators** writing school funding formulas
- **Education advocacy organizations** (EdTrust, EdBuild, NEPC)
- **Civil rights organizations** tracking funding equity and racial justice
- **Education journalists** covering school funding

## Data Sources

| Source | Description |
|---|---|
| [NCES Common Core of Data (CCD)](https://nces.ed.gov/ccd/) | School and district characteristics, demographics |
| School-Level Finance Survey (SLFS) | Per-pupil spending at the school level (ESSA-mandated) |
| [Census Annual Survey of School System Finances](https://www.census.gov/programs-surveys/school-finances.html) | District-level revenue sources and expenditures |
| [School Finance Indicators Database](https://schoolfinancedata.org/) | State-level funding equity and adequacy measures |
| [Civil Rights Data Collection (CRDC)](https://ocrdata.ed.gov/) | Equity data: access to courses, discipline, teacher quality |

## Key Papers

- Baker & Knight (2025) — Does money matter? Education funding and student outcomes
- EdTrust (2022) — Equal is not good enough: within-district funding inequities
- Jackson (2021) — School spending and student outcomes (Quarterly Journal of Economics)
- Education Law Center — Making the Grade: annual state funding report
- Albert Shanker Institute — School funding equity analysis

## Open Source Adjacencies

- School Finance Indicators Database — R/Stata research tools
- [NCES Data Tools](https://nces.ed.gov/ccd/elsi/) — Query tools (proprietary frontend, open data)
- [edbuild-map](https://edbuildna.org/content/category/tools) — School district funding map
- education-data-package — Education data wrappers
- [DecisionLab/funding-formula-simulator](https://github.com/DecisionLab) — State formula simulation research

## Success Criteria

- Import and visualize ESSA school-level spending data for one state's 1,000+ schools
- Identify within-district equity gaps (high-poverty vs. low-poverty schools) with 95% confidence
- Power a what-if simulation that produces results matching the state's official formula calculation
- Generate an advocacy brief in under 30 seconds ready for a school board meeting
- Support drill-down from state → district → school in under 3 clicks
- Detect and flag data quality issues in state submissions

## Skills Needed

- **Full-stack development** (React/Vue + Python/R backend)
- **Data visualization** (D3.js, Vega-Lite, or Observable Plot for charts/maps)
- **Statistical analysis** (funding equity metrics, Gini coefficients, regression)
- **Education policy domain knowledge** (state funding formulas, ESSA, Title I)
- **Data engineering** (multi-source ETL, 50-state data normalization)
- **What-if simulation design** (formula parameter modeling, sensitivity analysis)

## Risks

- **Data quality:** School-level spending data is new (post-ESSA). Many states report inconsistently or with errors. Data quality flagging is essential.
- **Formula complexity:** State funding formulas can be 50+ pages of legislation. Modeling them faithfully is a significant engineering challenge.
- **50-state scale:** Even the MVP targets one state, the range of formula types (foundation, power-equalizing, student-weighted, etc.) is vast.
- **Political sensitivity:** Funding equity analysis is politically charged. Frame as transparency, not advocacy. Let the data speak.
- **Data lag:** NCES data is typically 1–2 years behind. Users want current-year data. Need methodology notes and caveats.
