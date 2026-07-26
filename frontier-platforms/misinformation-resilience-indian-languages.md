---
track: frontier-platforms
status: published
---

# Misinformation Resilience Platform for Indian Languages

> India has 800M+ internet users — half of whom consume content in regional languages. Misinformation in Hindi, Tamil, Bengali, and Marathi spreads unchecked through WhatsApp and YouTube, with no open multimodal detection platform.

## The Problem

India is WhatsApp's largest market with over 500 million users, and the platform is the primary vector for misinformation in the country. Communal violence has been triggered by fabricated videos. Vaccine hesitancy has been amplified by false medical claims shared in regional languages. Elections have been contested on the basis of AI-generated deepfakes of candidates. Yet the tools to detect and counter this misinformation are overwhelmingly English-only and designed for Western social media platforms.

The challenge is three-dimensional. **Linguistic**: India's 22 scheduled languages and hundreds of dialects mean that misinformation mutates across languages — a false claim in Hindi is re-narrated in Tamil WhatsApp groups within hours. **Multimodal**: A deepfake video shared on YouTube links to a fabricated news article with an AI-generated image — each modality needs separate detection that must be correlated. **Platform fragmentation**: The same piece of misinformation spreads through WhatsApp, YouTube, Facebook, and ShareChat simultaneously, but each platform requires different APIs and access methods.

Existing fact-checking organisations (BOOM, Alt News, SM Hoax Slayer, Vishvas News) manually debunk claims but cannot scale to the volume of misinformation. AI4Bharat and other research groups have built Indic NLP datasets, and Shakti (a fact-checking shared task) has produced benchmarks. What does not exist is an integrated open-source platform that fuses multimodal detection (text, image, video) across Indian languages with a user-friendly interface for fact-checkers, journalists, and the public.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| BOOM / Alt News / SM Hoax Slayer | Manual fact-checking; cannot scale; English/Hindi bias |
| Google Fact Check Explorer | Second-level curation; doesn't detect new claims; limited Indian language support |
| Shakti shared task datasets | Research benchmarks; no production pipeline or API |
| AI4Bharat IndicNLP | NLP models and datasets; not a fact-checking platform |
| WhatsApp fact-checking helplines | Reactive (user must forward); can't proactively scan public channels |
| GPT-4 / Claude fact-checking | English-optimised; expensive at scale; no multimodal correlation for Indian contexts |

## What to Build

- **Cross-lingual claim detection**: Monitor public WhatsApp groups (opt-in), YouTube comments, and social media for claim-worthy statements in Hindi, Tamil, Bengali, Marathi, and other major Indian languages using IndicNER + mBERT/XLM-R
- **Multimodal verification pipeline**: Given a claim from a video, verify against (a) text sources via retrieved context, (b) image forensics (reverse image search, metadata analysis, deepfake detection with Deepware), (c) audio deepfake detection (RawNet2 or similar)
- **Claim matching across languages**: Match Hindi claim "हल्दी COVID को ठीक करती है" with its Tamil variant "மஞ்சள் COVID-ஐ குணப்படுத்துகிறது" — clustering same-claim-across-languages for coordinated debunking
- **Stance detection and propagation tracking**: Given a claim, track which social accounts amplify it, how fast it spreads, and whether the stance shifts across communities
- **Automated debunk draft generator**: For verified false claims, generate debunk drafts in the same language(s) with cited evidence, ready for fact-checker review
- **WhatsApp + YouTube monitoring interface**: Dashboard for fact-checking organisations to see trending unverified claims by language, region, and platform

**MVP (3-4 months solo):** Cross-lingual pipeline ingesting YouTube comments + public WhatsApp groups (opt-in) for Hindi + Tamil → claim extraction → text-based fact-checking against verified sources → dashboard.

## Stakeholders

- **800M+** Indian internet users, half consuming content in regional languages
- **15+** Indian fact-checking organisations (BOOM, Alt News, SM Hoax Slayer, Vishvas News, Fact Crescendo, etc.)
- **Election Commission of India** — monitoring misinformation during elections
- **Platforms** — WhatsApp, YouTube, Google, ShareChat (potential data-sharing partners)
- **Journalists** covering misinformation trends
- **Civil society organisations** working on communal harmony and public health communication

## Data Sources

| Source | Description |
|--------|-------------|
| [AI4Bharat IndicNLP Catalog](https://github.com/AI4Bharat/indicnlp_catalog) | Datasets, embeddings, and models for 10+ Indian languages |
| [Shakti Fact-Checking Dataset](https://shakti.github.io/) | Shared task dataset for fact-checking in Indian languages |
| [Multilingual Fake News Dataset (Zenodo)](https://zenodo.org/records/11408512) | Gujarati, Hindi, Marathi, Telugu fake news with labels |
| [YouTube Data API](https://developers.google.com/youtube/v3) | Comment scraping for misinformation monitoring |
| [Alt News / BOOM archives](https://www.altnews.in/) | Verified fact-checks in Hindi and English (scraped with permission) |
| [Deepware Scanner (open-source)](https://deepware.ai/) | Open-source deepfake detection (video and audio) |
| [NASSCOM / MeitY](https://www.meity.gov.in/) | India's proposed misinformation regulation framework |

## Key Papers

1. Patil, K. et al. (2024). *Multilingual Fake News Detection Dataset: Gujarati, Hindi, Marathi, and Telugu*. Zenodo.
2. Srihari, V.K. et al. (2025). *Detecting Fake News in Dravidian Languages*. ACL DravidianLangTech.
3. AI4Bharat (2023). *IndicNLP: Language Models and Datasets for Indian Languages*. ACL.
4. Shaar, S. et al. (2022). *That is a Known Lie: Detecting Previously Fact-Checked Claims*. ACL.
5. Alam, F. et al. (2024). *Multimodal Misinformation Detection: A Survey*. ACM Computing Surveys.

## Open Source Adjacencies

- [AI4Bharat IndicNLP](https://github.com/AI4Bharat/indicnlp_catalog) — Models and datasets for 10+ Indian languages
- [Deepware Scanner](https://github.com/Deepware-AI/deepware-scanner) — Open-source deepfake detection
- [Google Fact Check Tools API](https://developers.google.com/fact-check/tools/api) — API for previously fact-checked claims
- [YouTube Data API](https://developers.google.com/youtube/v3) — Comment and video metadata access
- [SpeechBrain / RawNet2](https://github.com/speechbrain/speechbrain) — Audio deepfake detection models
- [LangChain / LlamaIndex](https://www.langchain.com/) — RAG pipeline for evidence retrieval

## Skills Needed

- NLP / cross-lingual representation (mBERT, XLM-R, IndicBERT, LaBSE)
- Multimodal ML (vision transformers, audio deepfake, cross-modal fusion)
- Python (FastAPI, HuggingFace Transformers, PyTorch)
- Social media APIs (YouTube, optional WhatsApp Business API)
- Web frontend (React dashboard for fact-checkers)
- Fact-checking domain knowledge (ClaimRank, Verite, Q2A methodology)

## Risks

| Risk | Mitigation |
|------|------------|
| WhatsApp end-to-end encryption prevents content monitoring | Only monitor public WhatsApp channels/groups where users opt-in; reference reports from users who forward suspicious content to the system |
| Indian language NLP model quality varies by language | Start with Hindi and Tamil (best-resourced); use few-shot cross-lingual transfer for lower-resource languages |
| AI-generated deepfakes evolve faster than detection models | Build adversarial training loop: known deepfake techniques added to training data; publish model card with known failure modes |
| Fact-checkers may resist AI-assisted tools | Design as assistive (draft generator, not replacement); maintain human-in-the-loop for all published debunks |
| Platform API restrictions (YouTube comment rate limits, WhatsApp limits) | Caching and smart polling; multiple API keys; browser automation fallback |
