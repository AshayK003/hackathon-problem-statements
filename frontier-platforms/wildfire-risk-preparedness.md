---
track: frontier-platforms
status: published
---

# Frontier 08 — Wildfire Risk Assessment & Community Preparedness Platform

> 80M US properties face wildfire risk. 2025 destroyed 18,385 structures (16,324 in SoCal alone). Insurance crisis accelerating. No open-source platform combines satellite feeds, weather, fuels data, parcel risk scoring, and mitigation ROI optimization.

## The Problem

Wildfires are worsening (climate change: 2-5x more acres than 50 years ago). FAIR Plan (insurer of last resort) surging as carriers non-renew at record rates. Homeowners don't know which mitigation actions (defensible space? home hardening?) have the best ROI. Community Wildfire Protection Plans (CWPPs) are still created manually by consultants at $20K+ each. All data is publicly available — NASA, USGS, NOAA, LANDFIRE — but no open-source platform ingests it into actionable property-level intelligence.

## Why Existing Solutions Fail

| Tool | Limitation |
|------|-----------|
| **NASA FIRMS** | Point-based hotspots only, no risk scoring |
| **Wildfire Risk to Communities** | 270m resolution (too coarse for parcels), static |
| **First Street Fire Factor** | Commercial/closed, no mitigation optimization |
| **Planscape** | Landscape-level only, no homeowner interface |
| **PyreCast** | Real-time spread only, not risk/preparedness |
| **EFFIS** | Europe-only |

## What to Build

- Data fusion pipeline: NASA FIRMS/VIIRS + HRRR weather + LANDFIRE fuels + USGS topography
- Parcel-level risk scoring: XGBoost trained on historical burn + fuel + weather + topography
- Mitigation ROI optimizer: per-parcel ranked costed actions by risk reduction per dollar
- Community-level fuel treatment optimizer
- Evacuation planning: fire spread probability + road networks

**MVP (3-5 months solo):** Data pipeline → risk scoring model → mitigation ROI calculator → homeowner web map (MapLibre GL)

## Stakeholders

- 80M US property owners at wildfire risk
- 364M US residents affected by smoke annually
- 50+ insurance companies managing wildfire exposure
- 11,000+ fire departments
- 20M+ homes in Wildland-Urban Interface

## Data Sources

| Source | Description |
|--------|-------------|
| NASA FIRMS (VIIRS/MODIS) | 375m-1km fire hotspots, 2x/day, free API |
| Open-Meteo / NOAA HRRR | 3km hourly weather, free API |
| LANDFIRE | 30m fuels, vegetation, topography |
| USGS Wildfire Polygons | Historical perimeters (1800s-present) |
| USGS 3DEP | 10m/30m elevation |
| CAL FIRE FRAP | CA historical perimeters |

## Key Papers

- Xu et al. (2025) — "Deep Learning for Wildfire Risk Prediction" — *ISPRS J Photogrammetry*
- USC Generative AI for Wildfire Spread (2024) — CNN encoder-decoder
- DSS for Community Resilience Review (2024) — *Heliyon*
- First Street Foundation Fire Model (2022) — *MDPI Fire*. Peer-reviewed burn probability
- Wildfire Management Optimization PRISMA Review (2026) — *Springer*. 177 papers

## Open Source Adjacencies

- [Planscape](https://github.com/OurPlanscape/Planscape) — Apache 2.0, landscape resilience planning
- [ForeFire](https://github.com/forefireAPI/forefire) — GPLv3, wildfire simulation engine
- [BC WPS](https://github.com/bcgov/wps) — Apache 2.0, full predictive services platform
- [PyreCast](https://github.com/OpenFire/pyrecast) — Real-time fire spread forecast

## Skills Needed

- Geospatial data processing (PostGIS, GDAL, Rasterio)
- ML (XGBoost, spatial CV)
- OpenAPI map visualization (MapLibre GL)
- Python + FastAPI
- Meteorology/fire science domain knowledge

## Risks

- LANDFIRE updates every 3-5 years — stale fuels degrade accuracy
- Cloud cover masks satellite detection
- Risk accuracy affects property values/insurance — liability exposure
- First Street has 100M+ simulated fires and 5+ years R&D head start
- County government sales are slow (12-18 month cycles)
