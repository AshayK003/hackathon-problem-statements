---
track: frontier-platforms
status: published
---

# Personalized Learning Path Generator for Under-Resourced Students

> India's learning poverty rate is 55% — more than half of 10-year-olds cannot read a basic text. 260 million children are enrolled in school, but grade-level teaching ignores that most are 2-3 grades behind. No open-source system adapts curriculum to actual competency.

## The Problem

India's education system serves 260 million students across 1.5 million schools — the largest in the world. Yet the Annual Status of Education Report (ASER) has consistently shown for 15+ years that grade-level competence is the exception, not the rule. In 2024, only 42% of Class 5 children in rural India could read a Class 2 text. The National Achievement Survey (NAS) confirms this learning gap persists across states and subjects.

The core structural problem is that curriculum delivery is fixed to grade level, not actual competency. A Class 7 student who never mastered fractions sits in maths class learning algebra. A Class 4 student reading at Class 1 level is expected to comprehend Class 4 passages. Remedial teaching exists in policy (NIPUN Bharat, FLN mission) but is not operationalised at scale — teachers are too stretched to create individualised practice materials for 40+ students at different levels.

DIKSHA, the government's digital education platform built on Sunbird, has thousands of pieces of content aligned to the NCERT curriculum. But it is a content repository, not a personalised tutor. It does not assess a student's actual level, generate custom practice problems at that level, or adapt as the student progresses. The NEP 2020 explicitly calls for competency-based learning, but the operational tools to deliver it at scale do not exist.

An LLM-powered system can bridge this gap: assess the student's actual competency level (via a short adaptive test), map it to the relevant NCERT learning outcome, generate custom practice problems, explanations, and next steps — in the student's home language, at their pace, on whatever device they have access to (a shared smartphone, a government tablet, or a printout).

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| DIKSHA (Sunbird platform) | Content repository; no personalisation, no assessment, no adaptive path |
| BYJU'S / Vedantu | Paid (₹10K-50K/year); English-medium; designed for ahead-of-grade, not remediation |
| ASER / NAS assessments | Annual diagnostic only; no continuous assessment or practice generation |
| NIPUN Bharat / FLM guidelines | Policy documents; no operational software for teachers to implement |
| Khan Academy | English-first; limited India curriculum alignment; no Indian language content at scale |
| Teacher-driven remediation | One teacher, 40+ students at different levels; not feasible without tool support |

## What to Build

- **Adaptive competency assessment**: Short diagnostic (10-15 questions) that identifies student's actual learning level for each subject (maths, language) — outputs an ASER-equivalent level
- **Personalised practice generation**: Given student's actual level + target grade-level outcome, LLM generates custom practice problems, worked examples, and explanations at the right difficulty (using NCERT curriculum alignment)
- **Progress tracking per learning outcome**: Map every practice attempt to specific NCERT learning outcomes; show teacher/parent/student what's been mastered and what's next
- **Multilingual delivery**: Content generated in Hindi + 8 major regional languages; voice output option for low-literacy students
- **Offline-first mobile app**: Works on shared smartphones and government tablets (Aakash); content syncs when connected
- **Printable worksheets**: Weekly print-ready worksheets for students without device access, generated based on their level
- **Teacher dashboard**: "Your Class 5 section: 3 students are at Class 2 level in maths, 12 at Class 3, 18 at Class 4, 7 at Class 5 — here are custom practice sets for each group"

**MVP (3-4 months solo):** Adaptive assessment for Class 3-5 maths → personalised practice generation via LLM → Hindi + English output → offline mobile web app → teacher dashboard with 1 class pilot.

## Stakeholders

- **260 million** students enrolled in Indian schools
- **9.7 million** teachers across government schools
- **1.5 million** schools (mostly government)
- **NCERT, SCERTs, and state education departments**
- **NITI Aayog and MoE** — NEP 2020 and NIPUN Bharat implementation
- **NGOs** — Pratham (ASER), Azim Premji Foundation, Eklavya, Teach For India
- **EdTech DPI** — DIKSHA, Sunbird, and the proposed EduSAT platform

## Data Sources

| Source | Description |
|--------|-------------|
| [NCERT textbooks](https://ncert.nic.in/textbook.php) | All subjects, classes 1-12 (open-licensed, downloadable) |
| [DIKSHA / Sunbird](https://diksha.gov.in/) | 100K+ pieces of learning content (open, accessible via API) |
| [ASER reports](https://asercentre.org/) | Annual learning level data (rural India, reading + arithmetic) |
| [NAS reports](https://nas.gov.in/) | National Achievement Survey, class 3/5/8/10 subject-wise |
| [NROER](https://nroer.gov.in/) | National Repository of Open Educational Resources |
| [NIPUN Bharat FLN targets](https://www.education.gov.in/nipun-bharat) | Foundational Literacy and Numeracy goals and benchmarks |

## Key Papers

1. ASER Centre (2024). *Annual Status of Education Report (Rural)*. Pratham Foundation.
2. NCERT (2023). *National Achievement Survey 2021: Report*. Government of India.
3. World Bank (2024). *Learning Poverty in India: Trends and Interventions*. World Bank Group.
4. NITI Aayog (2023). *School Education Quality Index*. Government of India.
5. Muralidharan, K. et al. (2023). *Technology and Learning Outcomes: Experimental Evidence from India*. J-PAL.

## Open Source Adjacencies

- [Sunbird ED](https://sunbird.org/) — Open-source learning platform (DIKSHA is built on this)
- [Kolibri](https://learningequality.org/kolibri/) — Offline learning platform deployed in 200+ countries
- [NCERT e-textbooks](https://ncert.nic.in/textbook.php) — EPUB and PDF formats, open license
- [Open Assistant / LLM fine-tuning](https://open-assistant.io/) — Open-source instruction-tuned models for education
- [Pensieve (Memrise)](https://github.com/htkseason/pensieve) — Spaced repetition algorithm reference implementation
- [Riiid AIEd Challenge](https://www.kaggle.com/c/riiid-test-answer-prediction) — Knowledge tracing open dataset

## Skills Needed

- LLM fine-tuning / prompt engineering (educational content generation, assessment design)
- Knowledge tracing / adaptive testing (IRT, Bayesian Knowledge Tracing, DKT)
- Full-stack development (React Native for mobile, Python/Node backend)
- Offline-first architecture (PouchDB/CouchDB, service workers, content sync)
- UI/UX for low-literacy users (voice input, icon-based navigation, minimal text)
- Indian language NLP / TTS (AI4Bharat Indic-TTS, Dhwani)

## Risks

| Risk | Mitigation |
|------|------------|
| LLMs can hallucinate incorrect educational content | All generated content passes through a curriculum-verification step: cross-check against NCERT textbooks; teacher-review interface for new content |
| Adaptive assessment needs reliable IRT/knowledge tracing without large pilot data | Start with rule-based adaptive branching (correct → harder, wrong → easier); add ML knowledge tracing after 1,000+ students |
| Low smartphone access in target population | Offline-first mobile web; printable worksheets; shared-device mode with student profiles |
| Teacher resistance to AI in classroom | Design as teacher-augmentation not replacement; teacher dashboard gives control; co-design with 5-10 pilot teachers |
| NCERT curriculum changes state by state (some states use state board, not CBSE) | Build curriculum abstraction layer; start with CBSE/NCERT, add state curricula as modules |
