---
track: global-south-impact
status: published
---

# Harmful Algal Bloom Early Warning & Water Quality Platform

> Climate Adaptation | Water Systems — 8–10 month build

## The Problem

Harmful algal blooms (HABs) are increasing globally at an alarming rate due to climate change, agricultural runoff, and rising water temperatures. Currently, 60% of US lakes have HAB risks, and the problem is accelerating worldwide — threatening drinking water supplies, fisheries, tourism, and aquatic ecosystems. Cyanotoxins produced by blooms can contaminate drinking water, causing liver damage, neurological effects, and in extreme cases, death. Over 2 billion people worldwide drink untreated surface water. Most lakes in LMICs are completely unmonitored, while even monitored lakes in high-income countries rely on infrequent manual sampling that misses bloom onset. An AI-powered early warning system that fuses satellite imagery, weather forecasts, river discharge data, and nutrient loading estimates could provide 5–10 day advance warning of bloom events for both monitored and unmonitored water bodies.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| Manual water sampling & lab analysis | Expensive ($200–500/sample); infrequent (weekly at best); misses rapid bloom onset |
| Satellite chlorophyll-a monitoring (e.g., Copernicus Marine) | Only works on large water bodies (>1 km²); cloud cover obscures data; no forecasting |
| USGS / NOAA HAB forecasts | Available only for a handful of well-studied lakes (e.g., Lake Erie, Lake Okeechobee); not transferable |
| Simple chlorophyll concentration thresholds | High false positive rate; doesn't account for local ecology, mixing, or toxin production potential |
| LMIC water quality monitoring programs | Virtually nonexistent in most regions; limited to capital city water utilities at best |
| Citizen science bloom reporting apps (e.g., BloomWatch) | Reactive, sparse, no predictive capability |

## What to Build

- **Multi-modal fusion model** combining satellite imagery (Sentinel-2 OLI, Sentinel-3 OLCI), weather forecasts (ERA5), river discharge, nutrient loading (nitrogen/phosphorus), and lake morphology data
- **Transfer learning from monitored to unmonitored lakes** — train on data-rich US/European lakes (with in-situ validation), adapt to LMIC lakes with no ground truth using domain adaptation methods
- **Ensemble model architecture** — XGBoost for tabular features + LSTM on satellite time series + physics-informed neural network incorporating thermal stratification and nutrient dynamics
- **5–10 day probabilistic bloom forecast** — output bloom probability (low/medium/high) with uncertainty quantification, toxin production risk, and spatial extent estimate
- **Early warning dashboard** — for water utility managers, public health officials, and communities, with SMS/voice alerts for low-connectivity settings
- **Open API** — allowing integration into national water quality monitoring platforms and humanitarian early warning systems

## Stakeholders

- **200+ million Americans** who rely on lakes and reservoirs for drinking water
- **2+ billion people globally** who drink untreated surface water, especially in SSA and South Asia
- **Water utility managers** needing to time treatment adjustments (activated carbon, chlorination) before bloom arrival
- **Public health authorities** needing to issue boil-water advisories and health warnings
- **Fisheries and aquaculture operators** whose livelihoods depend on water quality
- **NOAA, USGS, NASA, ESA** — agencies with satellite missions and in-situ monitoring programs
- **LMIC national water resources authorities** with monitoring mandates but limited capacity

## Data Sources

- **NASA CyFi (Cyanobacteria Assessment Network)** — 500K+ labeled satellite image patches across US lakes with cyanobacteria cell count estimates
- **USGS HAB Data** — 40+ years of in-situ water quality sampling at thousands of US monitoring stations
- **NOAA Lake Erie HAB Forecast data** — most intensively studied bloom system globally; daily forecasts and in-situ validation
- **Sentinel-2 (ESA) MSI** — 10–60m resolution, 5-day revisit, ideal for lake monitoring
- **Sentinel-3 (ESA) OLCI** — 300m resolution, daily revisit, optimized for water quality (chlorophyll-a, turbidity, cyanobacteria index)
- **ERA5 (Copernicus)** — global atmospheric reanalysis with hourly weather variables (temperature, wind, precipitation, radiation)
- **Global River Discharge Database (GRDC)** — 9,500+ stations with historical discharge data for nutrient loading estimation
- **USGS WaterQualityData** — 18M+ nutrient concentration samples (nitrogen, phosphorus) from US water bodies

## Key Papers

- Bloomformer-2 (2024) — "Transformer-based spatiotemporal forecasting for harmful algal blooms using satellite data with application to Lake Erie and Utah Lake"
- NASA ESDS (2024) — "Cyanobacteria Assessment Network (CyAN): satellite-based early warning for freshwater harmful algal blooms" — technical summary of the NASA CyFi dataset and approach
- Sheikh, M. et al. (2024) — "Transfer learning for lake water quality monitoring in data-sparse regions: adapting deep learning models from well-monitored to unmonitored lakes"
- Ho, J. & Michalak, A. (2020) — "Challenges in tracking harmful algal blooms: a satellite view" — comprehensive review of remote sensing approaches and limitations

## Open Source Adjacencies

- **CyFi** (github.com/drivendataorg/cyfi) — open-source codebase for cyanobacteria detection from satellite imagery (DrivenData competition baseline)
- **EuroSAT** — open satellite image benchmark dataset for land use / land cover classification (useful for lake identification)
- **PyTorch / PyTorch Lightning** — deep learning framework for model development
- **XGBoost / LightGBM** — gradient boosting for tabular feature learning
- **Sentinel-Hub / EO-Learn** — open tools for satellite data access and preprocessing
- **HydroSHEDS / MERIT Hydro** — global hydrography datasets for river/watershed modeling
- **Flopy** — Python interface to MODFLOW for physics-informed groundwater-surface water modeling

## Success Criteria

- [ ] Ensemble model achieves AUC ≥ 0.85 on CyFi test set for cyanobacteria presence classification
- [ ] Transfer learning to unsupervised LMIC lakes achieves within 10% of supervised performance in 3 target countries
- [ ] Forecast model provides usable predictions 5 days in advance with ≥ 75% precision on bloom events (validated against in-situ data where available)
- [ ] Dashboard deployed and tested with ≥ 5 water utility managers or public health officials
- [ ] SMS/voice alert system operational with < 5 minute latency from model prediction to end-user notification
- [ ] Open API documented and publicly accessible with ≥ 2 external integrations demonstrated

## Skills Needed

- 2× ML Engineers (remote sensing time-series, spatiotemporal models, transfer learning, ensemble methods)
- 1× Data / ML Engineer (satellite data pipelines, EO-Learn / Sentinel processing, large-scale geospatial data)
- 1× Water Quality / Limnology Domain Expert (HAB science, toxin dynamics, USGS/NOAA monitoring context, LMIC water systems)

## Risks

| Risk | Mitigation |
|---|---|
| Cloud cover blocks satellite imagery for days/weeks in tropical regions | Integrate weather forecasts to anticipate cloud gaps; use SAR (Sentinel-1) as complementary data source; build temporal interpolation into models |
| No in-situ validation data for LMIC lakes | Use physics-informed models that don't require local training data; build confidence intervals into predictions; partner with local universities for opportunistic sampling |
| Harmful algal blooms are complex — satellite may detect algae but not toxin production | Explicitly model toxin production risk as separate output from biomass; incorporate environmental toxin-production triggers (temperature, light, nutrients, pH) |
| Nutrient loading data unavailable in most LMICs | Estimate from satellite-derived land use and global fertilizer application datasets; build uncertainty into nutrient-dependent model components |
| Satellite revisit frequency insufficient for rapid bloom detection over small water bodies | Focus on larger lakes (>1 km²) for satellite-only approach; integrate weather-based proxies for bloom dynamics in smaller water bodies |
