---
track: global-south-impact
status: published
---

# Scientific Reproducibility Verification & Screening Engine

> Scientific Research | Open Science — 8–12 month build

## The Problem

Science is facing a severe reproducibility crisis. Only 36% of psychology studies and 51% of preclinical cancer studies can be replicated. An estimated $28 billion per year is wasted on irreproducible preclinical research. The causes are well-documented: p-hacking (data dredging until results become significant), HARKing (Hypothesizing After Results are Known), cherry-picking (selectively reporting favorable outcomes), underpowered studies, and data manipulation — including image manipulation present in 10%+ of published papers. Current quality assurance relies on peer review — an unpaid, overloaded system that catches only the most obvious issues. No automated, scalable solution exists that can screen manuscripts at submission or published papers for statistical red flags, verify computational reproducibility, check data and figure integrity, and flag potential integrity issues before they become entrenched in the literature.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| Traditional peer review | Overloaded (each reviewer works for free); no statistical training for many reviewers; catches <1% of issues |
| statcheck (automated statistical error detection) | Only detects p-value inconsistencies in APA-formatted papers; misses p-hacking, HARKing, image manipulation |
| Manual reproducibility efforts (e.g., eLife Reproducibility Project) | Slow, expensive ($10K+ per paper); not scalable to millions of papers |
| Plagiarism detection (Turnitin, iThenticate) | Only checks text copying; no statistical or data integrity checks |
| Post-publication peer review (PubPeer) | Reactive, non-systematic, no automated screening |
| Journal data/code policies | Rarely enforced; no automated verification infrastructure |
| Retraction Watch | Tracks retractions but does not predict or prevent them; reactive by design |

## What to Build

- **LLM-based statistical integrity agent** — screen manuscripts for common statistical errors: p-hacking indicators (p-value bunching near .05), HARKing signals (methods/results inconsistency), cherry-picking (selective outcome reporting), and sample size/effect size anomalies
- **Sandboxed code execution environment** — securely run code from papers in isolated containers, verify outputs against reported results, and flag discrepancies
- **Figure integrity analyzer** — automated detection of duplicated/spliced images, inappropriate image manipulation (Western blot splicing, flow cytometry gate manipulation), and figure-data consistency checks
- **Data provenance scanner** — verify that reported data sources exist, have appropriate accessions, and match described methodology
- **Reproducibility risk score** — composite scoring system (1–100) integrating all above signals, with per-category breakdown visible to editors, peer reviewers, and readers
- **Publisher integration API** — designed as a web service that manuscript submission systems (e.g., ScholarOne, Editorial Manager) can call at submission time
- **Open science dashboard** — public leaderboard showing reproducibility scores by journal, institution, and research field

## Stakeholders

- **8.5+ million researchers** worldwide whose work is affected by unreliable findings
- **10,000+ academic journals** seeking to improve screening at submission
- **Research funders** (NIH, Wellcome, Gates, NSF) who waste $28B/year on irreproducible research
- **Universities and research institutions** seeking to protect their reputations and reduce retractions
- **Meta-scientists and methodologists** studying the replication crisis and seeking scalable solutions
- **Patients and the public** who rely on biomedical research for treatment decisions
- **Science publishers** (Springer Nature, Elsevier, PLOS, eLife, MDPI) looking for automated QA tools

## Data Sources

- **arXiv** — 2.5+ million preprints (math, CS, physics, statistics, quantitative biology), with LaTeX source code for analysis
- **PubMed Central (PMC) OA subset** — 5+ million full-text articles with figures available for analysis
- **PubPeer** — post-publication peer review comments, including identified statistical and methodological issues
- **Retraction Watch Database** — 40,000+ retracted papers with reasons (fabrication, plagiarism, fake peer review, unreliable data)
- **Statcheck meta-analysis corpus** — database of statistical reporting errors from 250,000+ psychology papers
- **Bik et al. (2016) image manipulation dataset** — ground-truth labeled examples of problematic figure manipulations
- **Open Science Framework (OSF)** — registered reports, pre-registrations, and replication study metadata
- **CodeOcean / CodeRefinery** — repositories of executable scientific code for reproducibility testing

## Key Papers

- Nature Editorial (2023) — "The replication crisis: 15 years on" — state-of-the-field analysis of reproducibility challenges across disciplines
- Freedman, L. et al. (2015) — "The economics of reproducibility in preclinical research" — landmark study estimating $28B/year wasted
- Stanford/Harvard POPPER Project (2025) — "LLM-based detection of p-hacking and HARKing in published biomedical literature: a large-scale audit"
- Bik, E. et al. (2016) — "The prevalence of inappropriate image duplication in biomedical research publications" — found manipulation in 10%+ of papers across 40 journals
- Nuijten, M. et al. (2016) — "The prevalence of statistical reporting errors in psychology (1985–2013)" — meta-analysis using statcheck showing systematic error rates

## Open Source Adjacencies

- **statcheck** — R/JavaScript package for automatic detection of statistical reporting inconsistencies (foundational baseline for this project)
- **VerifyAI** — open-source toolkit for AI-generated content detection and verification
- **OpenProof.science** — open platform for computational reproducibility checks and provenance tracking
- **PaperQA** — RAG-based system for querying scientific papers; can be adapted for inconsistency checking
- **CodiMD / HedgeDoc** — collaborative markdown editor with version history (code execution testbed)
- **Docker / Singularity** — sandboxed execution for running code from papers
- **OpenCV / scikit-image** — image analysis for figure integrity checks

## Success Criteria

- [ ] LLM-based statistical integrity agent detects p-hacking indicators with ≥ 85% precision at 70% recall on held-out test set
- [ ] Figure integrity analyzer achieves ≥ 90% precision for duplicated image panels on the Bik et al. benchmark
- [ ] Sandboxed code execution runs and verifies outputs for ≥ 60% of submitted papers (code available + runnable)
- [ ] Reproducibility risk score correlates significantly with known retractions and PubPeer comments (validation study on 5,000+ papers)
- [ ] Pipeline processes a full manuscript in < 10 minutes on standard cloud infrastructure
- [ ] Deployed as API and integrated with ≥ 2 publisher submission systems or preprint servers
- [ ] Public dashboard operational with ≥ 10,000 scored papers

## Skills Needed

- 2× ML / NLP Engineers (LLM agents, statistical text analysis, fine-tuning, prompt engineering for scientific content)
- 1× Full-Stack Engineer (API design, sandboxed execution environment, dashboard, publisher integration)
- 1× Computational Reproducibility / Meta-Science Domain Expert (research methods, statistics for scientific publishing, publisher workflows)

## Risks

| Risk | Mitigation |
|---|---|
| False positives could wrongly flag valid research | Build confidence-calibrated scores, not binary flags; design for human-in-the-loop review; publish transparency reports on error rates |
| Researchers may game the system | Use ensemble of diverse signals; obfuscate detection algorithms; adversarial robustness testing before deployment |
| Code from papers rarely runs without intervention | Target the 60% that can run; integrate with CodeOcean/CodeRefinery; use error-tolerant partial verification for the rest |
| Publishers may resist automated QC of their workflow | Emphasize value for editors; offer tiered integration (from low-effort risk scoring to full pipeline); publish open standards |
| LLMs produce hallucinations in statistical analysis | Use chain-of-thought prompting + structured output with explicit statistical calculation verification; pass results through constraint-checking layer |
| Image manipulation detection requires labeled training data | Augment Bik et al. dataset with synthetic manipulations; use self-supervised learning on figure-splicing detection |
| Legal concerns about automated paper screening | Position as editorial decision support tool, not public judgment; work with publisher legal teams on liability frameworks |
