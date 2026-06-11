---
track: global-south-impact
status: published
---

# AI-Integrated Informal Waste Sector Platform for Circular Economy

> Environment | Urban Planning — 6–8 month build

## The Problem

Over 2 billion people worldwide lack access to formal waste collection services. An estimated 15–20 million informal waste pickers — one of the most marginalized workforces globally — earn $1–5 per day sorting and recycling materials from dumpsters and dumpsites. Meanwhile, 60% of all waste ends up in uncontrolled dumpsites or open landfills, causing severe environmental and health damage. The informal waste sector actually achieves recycling rates that rival or exceed formal systems in many cities, but waste pickers are excluded from city planning, exploited by middlemen, and lack the tools to optimize their routes, know material prices, or connect directly with buyers. No existing platform combines computer vision for material identification, route optimization, price prediction, and supply-demand matching specifically for the informal waste sector.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| Municipal waste management systems | Ignore informal sector entirely; designed for truck-based collection only |
| Recycling apps (e.g., RecycleNation, iRecycle) | US/EU-centric; assume formal curbside recycling; no offline mode; no informal worker UX |
| WhatsApp/phone-based waste trading | No quality verification; no price transparency; middlemen capture value; no route optimization |
| Web platforms (e.g., TrashCoin, Plastic Bank) | Require smartphones & internet; incentivize plastic only; ignore mixed waste and organic material |
| Formal waste aggregators | Pay pickers below-market rates; no data collection on material flows; no worker empowerment |

## What to Build

- **Mobile-first application** designed for low-literacy users with icon-based navigation, local language voice prompts, and full offline capability
- **Computer vision material identification** — use the phone camera to identify and quantify waste materials (plastic type, metal, glass, paper, organic) from a photo with quality grading
- **Offline route optimization** — plan collection routes that maximize material value per kilometer for waste pickers, using cached map data and real-time pickup requests
- **Price prediction & transparency** — ML models that predict fair market prices for each material category based on local market conditions, updated when connectivity is available
- **Supply-demand matching** — connect waste pickers directly with recyclers, manufacturers, and composting facilities, bypassing exploitative middlemen
- **City-level dashboard** — for urban planners and waste authorities to visualize informal sector material flows, estimate recycling rates, and integrate informal workers into formal policy

## Stakeholders

- **15–20 million informal waste pickers** globally, concentrated in South Asia, Sub-Saharan Africa, and Latin America
- **2+ billion people** lacking formal waste collection services
- **1,000+ cities** in LMICs with large informal waste sectors but no integration into municipal planning
- **Recyclers, manufacturers, and composting facilities** seeking consistent, high-quality feedstock
- **Municipal governments and urban planners** needing data on waste flows and recycling rates
- **Environmental and climate NGOs** working on plastic pollution, methane reduction, and circular economy

## Data Sources

- **World Bank — What a Waste 2.0** — global database of waste generation, composition, and management across 164 cities and 47 countries
- **TrashNet Dataset** — 2,527 images of 6 waste categories (glass, paper, metal, plastic, cardboard, trash)
- **Kaggle Waste Classification Data** — 25,000+ labeled images for waste type classification
- **OpenStreetMap** — building footprints, road networks for route optimization in informal settlements
- **WIEGO (Women in Informal Employment: Globalizing and Organizing)** — worker surveys, sector profiles, and policy reports on informal waste workers
- **UN-Habitat Waste Wise Cities** — city-level waste data collection tool and database

## Key Papers

- Wilson, D. et al. (2006) — "Role of informal sector recycling in waste management in developing countries" — foundational study establishing 15–20M worker estimate
- Harfadli, M. et al. (2024) — "Computer vision and IoT for waste classification: a systematic review" — comprehensive review of CV approaches adapted for LMIC contexts
- Medina, M. (2008) — "The informal recycling sector in developing countries: organizing waste pickers" — socio-economic framework and organizational models
- Velis, C. et al. (2012) — "Resource recovery from waste: business models for energy, nutrient and water reuse" — circular economy frameworks applicable to informal sector

## Open Source Adjacencies

- **TensorFlow / TFLite** — offline on-device model inference for material classification
- **OSRM (Open Source Routing Machine)** — open-source routing engine for route optimization with offline support
- **OpenRouteService** — open-source directions, isochrones, and route optimization
- **TrashNet / TrashNet-Expanded** — open datasets for waste classification model training
- **OpenMapFlow** — open-source map-matching and road network analysis for last-mile logistics

## Success Criteria

- [ ] CV material classifier achieves ≥ 90% accuracy across 6 material categories on held-out test data
- [ ] TFLite model runs in < 1 second on a $50 Android phone with no internet
- [ ] Route optimization reduces picker travel distance by ≥ 20% in pilot city simulation
- [ ] Price prediction model for 5 material categories achieves MAE ≤ 10% of market price in 2 test cities
- [ ] Field test with ≥ 10 waste pickers in one city shows ≥ 30% income increase over 4-week pilot
- [ ] Platform works entirely offline for core features; syncs data when connectivity available
- [ ] City dashboard produces material flow estimates validated against known local recycling data

## Skills Needed

- 1× Computer Vision Engineer (image classification, TFLite model optimization, mobile deployment)
- 1× ML Engineer (time-series price prediction, route optimization algorithms, demand forecasting)
- 1× Full-Stack Mobile Developer (cross-platform app, offline-first architecture, icon-based UI)
- 1× Urban Planning / Circular Economy Domain Expert (informal waste sector knowledge, LMIC policy context)

## Risks

| Risk | Mitigation |
|---|---|
| Waste pickers have low smartphone ownership | Target very low-end Android devices ($30–50); build SMS-based fallback for key features; partner with worker cooperatives for device access |
| Material classification is hard in uncontrolled conditions (lighting, background, moisture) | Train with data augmentation simulating dumpsite conditions; use ensemble of multiple photos per item |
| Price volatility in recyclable materials | Build confidence intervals into price predictions; focus on short-term (same-week) rather than long-term forecasts |
| Resistance from middlemen who extract value from the current system | Partner with waste picker cooperatives and municipalities; frame as worker empowerment, not market disruption |
| Varying waste composition by city/season | Design platform for city-specific model fine-tuning with local data; build active learning loops for CV model |
