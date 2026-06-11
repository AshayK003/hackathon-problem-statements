---
track: global-south-impact
status: published
---

# Offline-First AI Crop Disease & Pest Diagnostic for Smallholder Farmers

> Agriculture | Plant Health — 5–7 month build

## The Problem

Globally, crop diseases and pests cause 20–40% yield losses annually — a staggering $220 billion in economic damage. The FAO recommends one extension officer per 400 farms, but in Sub-Saharan Africa the ratio is closer to 1:5,000–50,000. Smallholder farmers in LMICs often cannot identify the diseases affecting their crops until it is too late, lack access to expert diagnosis, and have no reliable offline reference for treatment options. While AI-based plant disease diagnosis has been demonstrated in research (notably Mohanty et al. 2016), existing solutions require internet connectivity, are too large for low-end phones, cover only a narrow set of crops, or lack an integrated treatment recommendation system. An offline-first, ultra-lightweight AI diagnostic running entirely on $30 phones — with a comprehensive treatment knowledge base — could give 500+ million farming families access to expert-level crop disease identification.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| Agricultural extension officers | 1:5,000–50,000 ratio in SSA; visits every 6–12 months |
| Farmer-to-farmer knowledge sharing | Varies widely in accuracy; no systematic reference |
| Printed disease identification guides | Static; require literacy; only cover common diseases in a region |
| Web-based plant disease apps (Plantix, Agrio) | Require internet; limited to well-studied crops; often region-specific |
| Academic plant disease AI models | 100MB+ models; assume high-end hardware; no treatment integration |
| SMS-based services (e.g., MFarm, Esoko) | Text-only; no image diagnosis; limited crop coverage |

## What to Build

- **Ultra-lightweight TFLite/ONNX model** (2–5 MB) for on-device plant disease classification, optimized for $30–50 Android phones
- **Multi-modal diagnosis** fusing phone camera image + farmer-reported location + current season + crop growth stage for improved accuracy
- **Transfer learning from PlantNet** (world's largest plant image database) to bootstrap crop and disease coverage, then fine-tune on LMIC-specific disease datasets
- **Offline treatment knowledge base** — a curated, locally-stored database of treatment recommendations (organic, chemical, cultural control) for each disease-crop pair, in local languages
- **Icon-based + voice-guided UI** — designed for low-literacy users with local language voice prompts and intuitive icons for navigation
- **Disease surveillance dashboard** — anonymized disease reports aggregated for agricultural ministries and extension services to track outbreak patterns in real-time
- **Continuous learning via semi-supervised feedback** — farmers can upload follow-up photos of treatment outcomes; model uses consistency regularization to improve with each cycle

## Stakeholders

- **500+ million smallholder farming families** in LMICs who lack access to crop disease expertise
- **Agricultural extension services** in SSA and South Asia seeking scalable tools to amplify reach
- **National plant protection organizations** (phytosanitary services) tracking pest and disease outbreaks
- **International agricultural research centers** (CGIAR, IITA, CIMMYT, IRRI) with crop-specific expertise
- **NGOs and development programs** (One Acre Fund, AGRA, TechnoServe) working with smallholder farmers

## Data Sources

- **PlantVillage Dataset (Penn State / EPFL)** — 54,306 images of 38 crop-disease pairs, the foundational public dataset for plant disease AI
- **IP102 (Insect Pest Classification)** — 75,000+ images of 102 insect pest species affecting major crops
- **CCMT (Cassava Leaf Disease / Cassava Disease Dataset)** — 50,000+ labeled images of cassava diseases from Uganda, Tanzania, and Kenya
- **DLCPD-25 (Deep Learning Crop Pest Dataset)** — 221,000 images covering 25 crop-pest pairs, including high-quality field photos
- **Cassava Disease Dataset (Makerere AI Lab)** — 21,000 labeled images from Uganda field conditions, used in global competition
- **PlantCLEF / PlantNet API** — 100K+ plant species image database for transfer learning backbone
- **FAO Plant Protection Database** — global pest and disease distribution records, treatment guidelines, and pesticide registrations

## Key Papers

- Mohanty, S. et al. (2016) — "Using deep learning for image-based plant disease detection" — foundational paper achieving 99.35% accuracy on PlantVillage dataset under controlled conditions
- Ramcharan, A. et al. (2017) — "Deep learning for image-based cassava disease detection in Tanzania" — first field deployment of AI disease diagnosis in SSA, achieving 93% accuracy
- Selvaraj, M. et al. (2019) — "AI-powered banana disease and pest detection in Africa" — multi-country validation across Uganda, Tanzania, and Kenya
- Hughes, D. & Salathé, M. (2015) — "An open access repository of images on plant health to enable the development of mobile disease diagnostics" — introduces PlantVillage dataset and mobile diagnostic vision

## Open Source Adjacencies

- **AgriEdge-AI** — open-source platform for AI-powered agricultural advisory in low-resource settings (closest existing project)
- **NASA Harvest** — open agricultural monitoring platform with pre-trained crop-type models
- **TFLite Model Maker** — Google's framework for building custom on-device ML models, with image classification template
- **TensorFlow / PyTorch Mobile** — deployment frameworks for on-device inference
- **PlantNet API** — open access to world's largest plant image database for transfer learning
- **ONNX Runtime Mobile** — cross-platform inference engine for model deployment

## Success Criteria

- [ ] Model achieves ≥ 92% top-3 accuracy across 30+ crop-disease pairs from PlantVillage, IP102, and CCMT held-out test sets
- [ ] TFLite model is ≤ 5 MB and runs inference in < 1 second on a $30 Android phone
- [ ] Offline treatment knowledge base contains actionable recommendations for ≥ 50 disease-crop pairs in ≥ 3 local languages
- [ ] Field pilot with ≥ 100 farmers across 2 SSA countries shows ≥ 20% reduction in crop loss from target diseases within one growing season
- [ ] UI usability validated with ≥ 10 low-literacy farmers (≤ 2 years of schooling) — task completion rate ≥ 85%
- [ ] Semi-supervised learning loop shows steady accuracy gains: ≥ 2% per month from farmer feedback images
- [ ] Full offline operation verified: all features work with zero internet connectivity

## Skills Needed

- 1× Computer Vision / ML Engineer (image classification, TFLite/ONNX model optimization, transfer learning, semi-supervised learning)
- 1× Mobile Developer (cross-platform app, offline-first architecture, local language voice UI, icon-based design)
- 1× Plant Health / Agronomy Domain Expert (crop disease diagnosis, treatment knowledge base curation, agricultural extension systems in LMICs)

## Risks

| Risk | Mitigation |
|---|---|
| Model accuracy drops significantly in real field conditions vs. controlled lab images | Use aggressive data augmentation simulating field conditions (lighting, blur, occlusion, background variety); collect field photos from early pilot for fine-tuning |
| Farmers have low-end phones with poor cameras | Set minimum camera resolution threshold; use confidence calibration so model can say "I'm not sure" and refer to extension officer in uncertain cases |
| Disease symptoms vary by region and variety | Build region-specific fine-tuning workflow; use location-aware model routing (different model per agro-ecological zone) |
| Treatment recommendations could be harmful if incorrect | Curate knowledge base with expert review; include safety warnings; prioritize organic/low-risk options; position as advisory, not prescription |
| Model becomes outdated as new diseases emerge | Design update mechanism; model can be updated via small delta patches when connectivity available; allow extension officers to seed new disease profiles |
