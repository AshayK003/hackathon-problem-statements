---
track: global-south-impact
status: published
---

# Ocean Plastic River Watch — Source-to-Sea Tracking Platform

> 1,000 rivers emit nearly 80% of the world's ocean plastic. Most are in Asia. No open-source platform fuses satellite imagery, river flow data, and waste generation models to identify where intervention will have the highest impact.

## The Problem

Approximately 8 million metric tons of plastic enter the ocean every year. Research by The Ocean Cleanup has identified 1,000 rivers globally — concentrated in Asia — that account for nearly 80% of this flow. The Ganges, Brahmaputra, Indus, and other South and Southeast Asian rivers are among the top contributors. This plastic travels from inland waste sources through river networks to the ocean, breaking into microplastics, entering food chains, and accumulating in garbage patches.

Current efforts to address ocean plastic are hampered by a fundamental data problem: we don't know precisely where the plastic comes from, which rivers are the worst offenders at which times of year, and which intervention points (waste collection, river barriers, recycling infrastructure) would have the highest ROI. The Ocean Cleanup uses research vessels, aerial drones, and satellite imagery to track plastic, but this is proprietary research, not an accessible decision-support tool. The World Bank and UNEP publish country-level estimates, but these are too coarse for local intervention planning.

What is needed is an open platform that fuses satellite imagery (Sentinel-2 for macroplastic detection, Landsat for land use), river discharge data (GRDC, local gauge stations), waste generation estimates (World Bank What a Waste, country-level data), and population density maps to identify high-emission river segments, predict peak plastic outflow months, and model the impact of interventions.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| The Ocean Cleanup research | Proprietary; limited to select river systems; not available as open tool |
| Global Plastic Watch (satellite) | Research platform; only covers macroplastic in a few regions; no river flow integration |
| World Bank / UNEP reports | Country-level aggregate; not actionable for local intervention planning |
| Academic studies (one-river papers) | Non-replicable; no consistent methodology across rivers |
| NASA CYGNSS microplastic detection | Experimental; ocean-only; can't pinpoint river sources |
| River plastic emission models (e.g., Jambeck equation) | Global estimates with high uncertainty; no real-time satellite validation |

## What to Build

- **River plastic emission model**: Fuse waste generation data (per capita × population in each river basin) with satellite land cover (urbanisation, waste site proximity) and river discharge to estimate monthly plastic emission per river segment
- **Satellite macroplastic hotspot detection**: Sentinel-2 imagery analysis (spectral unmixing + ML classification) to detect floating macroplastic accumulation zones in river channels and estuaries
- **Temporal outflow predictor**: Seasonal patterns — "Ganges at Patna peaks in plastic outflow during June-September monsoon" based on historical discharge + waste generation correlations
- **Intervention impact simulator**: "If a waste capture system is installed at bottleneck point X, Y% of river plastic is intercepted before reaching the ocean" — model effectiveness of river barriers, waste collection, and recycling infrastructure at any point in the river network
- **Dashboard for policymakers and NGOs**: Interactive global/regional map showing high-emission rivers, monthly outflow predictions, and intervention ROI rankings
- **Time-series monitor**: Track changes over years — is a given river getting cleaner or dirtier? Are interventions working?

## Stakeholders

- **~2 billion** people living within 50 km of plastic-emitting river systems (mostly in Asia and Africa)
- **National environmental agencies** (India: MoEFCC, CPCB; SE Asian counterparts)
- **River basin authorities** (Ganga, Mekong, Indus, Yangtze, etc.)
- **NGOs** — The Ocean Cleanup, Ocean Conservancy, Break Free From Plastic, WWF
- **Waste management companies and municipalities** in high-emission river corridors
- **UNEP and World Bank** — funding intervention programs
- **Fishing and tourism communities** directly affected by ocean plastic

## Data Sources

| Source | Description |
|--------|-------------|
| [Sentinel-2 (ESA)](https://scihub.copernicus.eu/) | 10m multispectral imagery → macroplastic detection in rivers (free, 5-day revisit) |
| [GRDC River Discharge](https://grdc.bafg.de/) | Global river discharge data from 10,000+ gauging stations |
| [World Bank What a Waste](https://datatopics.worldbank.org/what-a-waste/) | Country-level waste generation and composition data |
| [Global Plastic Watch](https://globalplasticwatch.org/) | Satellite-detected plastic waste sites (open data) |
| [Ocean Cleanup open research](https://theoceancleanup.com/research/) | River plastic emission estimates, published methods (open access papers) |
| [NASA CYGNSS](https://podaac.jpl.nasa.gov/CYGNSS) | Ocean microplastic concentration proxy (roughness dampening) |
| [WorldPop population density](https://www.worldpop.org/) | Basin-level population estimates for waste generation modeling |

## Key Papers

1. Meijer, L. et al. (2021). *More than 1000 rivers account for 80% of global riverine plastic emissions into the ocean*. Science Advances.
2. Lebreton, L. et al. (2019). *River plastic emissions to the world's oceans*. Nature Communications.
3. Perez-Garcia, A. et al. (2025). *River plastic hotspot detection from space*. iScience.
4. Biermann, L. et al. (2020). *Finding Plastic Patches in Coastal Waters using Optical Satellite Data*. Scientific Reports (Nature).
5. Jambeck, J. et al. (2015). *Plastic waste inputs from land into the ocean*. Science.

## Open Source Adjacencies

- [Global Plastic Watch (open data)](https://globalplasticwatch.org/) — Satellite-detected waste sites (dataset and methodology)
- [NASA CYGNSS microplastic data](https://podaac.jpl.nasa.gov/) — Ocean microplastic concentration maps
- [Sentinel-2 AWS Open Data](https://registry.opendata.aws/sentinel-2/) — Full Sentinel-2 archive on AWS (free to process)
- [Ocean Cleanup research data](https://theoceancleanup.com/research/) — Peer-reviewed papers with open methods
- [OSMnx](https://github.com/gboeing/osmnx) — River network extraction from OSM
- [HydroSHEDS](https://www.hydrosheds.org/) — Global watershed boundaries and river networks

## Success Criteria

- [ ] River plastic emission model covers ≥ 300 high-emission rivers (top 30% by estimated emissions)
- [ ] Satellite macroplastic detection validated against ground truth for ≥ 3 river systems (precision > 70%)
- [ ] Intervention impact simulator produces cost-benefit rankings for ≥ 5 intervention types
- [ ] Dashboard deployed with English + regional language support for top 5 emitter countries
- [ ] Temporal monitor shows annual trends for ≥ 5 years of historical data
- [ ] All model code open-source; data sources free and publicly accessible

## Skills Needed

- Remote sensing (Sentinel-2 processing, spectral unmixing, object detection in satellite imagery)
- Hydrology / river transport modeling (discharge, sediment transport equations, HEC-RAS or simpler)
- Python (rasterio, xarray, geopandas, scikit-learn, PyTorch for ML)
- Environmental science domain knowledge (waste management, polymer types, riverine transport mechanics)
- Web dashboard (React + Mapbox/MapLibre, deck.gl for 3D visualisation)

## Risks

| Risk | Mitigation |
|------|------------|
| Macroplastic is spectrally similar to floating vegetation, debris, and water surface features | Multi-sensor fusion (optical + radar) + temporal analysis (persistence over multiple passes) to distinguish plastic from organic matter |
| River plastic emission data is sparse for ground-truth validation | Model calibration against published field studies (The Ocean Cleanup, academic papers) per river system |
| Waste generation data at basin level has high uncertainty | Sensitivity analysis per input parameter; present results as ranges not point estimates |
| Intervention cost-benefit data is region-specific | Build cost-input interface where users plug in local costs; model provides expected reduction, user provides budget |
| Satellite revisit time (5 days for Sentinel-2) misses short-duration plastic transport events | Complement with hydrodynamic modeling that simulates transport between satellite observation days |
