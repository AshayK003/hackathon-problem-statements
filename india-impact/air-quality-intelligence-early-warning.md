---
track: india-impact
status: published
---

# Air Quality Intelligence & Early Warning System

> India has 22 of the world's 30 most polluted cities. 1.67 million deaths annually are attributable to air pollution. Yet there is no open-source platform that fuses ground monitors, satellite data, and weather forecasts into actionable ward-level intelligence.

## The Problem

India's air pollution crisis is well-documented: 22 of the world's 30 most polluted cities are Indian, and the country loses 1.67 million lives annually to air pollution-related diseases (Lancet, 2024). The economic cost exceeds $36 billion per year in lost productivity and healthcare expenditure.

The Central Pollution Control Board (CPCB) operates the Continuous Ambient Air Quality Monitoring System (CAAQMS) with 300+ real-time monitoring stations across major cities. The System of Air Quality and Weather Forecasting And Research (SAFAR) provides air quality forecasts. NASA and ISRO satellites (MODIS, Sentinel-5P, INSAT-3D) offer aerosol optical depth and atmospheric composition data. The India Meteorological Department (IMD) publishes gridded meteorological forecasts.

Each of these data sources exists in isolation. CPCB publishes raw hourly AQI numbers. SAFAR offers limited forecasts for select cities. Satellite data requires significant GIS expertise to process. Weather data is separate. No open-source platform fuses these sources into a unified model that can predict AQI at ward-level resolution 48 hours ahead and attribute sources (stubble burning vs. vehicles vs. industrial emissions vs. dust). City corporations and citizens are left with fragmented, reactive information.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| CPCB CAAQMS portal | Raw hourly numbers; no forecasting, no source apportionment, no ward-level granularity |
| SAFAR forecasts | Limited to 10 cities; no open API or model access |
| AQI.in / Ambee | Closed dashboards; no predictive model, no satellite fusion, paid APIs |
| IQAir / PurpleAir | Crowdsourced hardware; limited coverage in India, no integration with CPCB data |
| Google Air Quality API | API-key-gated; expensive at scale; no open-source model to build upon |
| NASA Giovanni / GEE | Requires significant remote sensing expertise; no India-specific product |

## What to Build

- **Data fusion engine**: Ingest CPCB (ground), MODIS/MAIAC (AOD), Sentinel-5P (NO₂, SO₂), ERA5 (meteorology), and IMD (weather forecasts) into a unified spatiotemporal dataset
- **Ward-level AQI nowcast**: Downscale sparse monitor readings to ward resolution using satellite AOD + land-use regression
- **48-hour AQI forecast**: Ensemble ML model (LightGBM + XGBoost + LSTM) trained on historic fused data
- **Source apportionment module**: PMF-based or ML-based attribution of pollution to sources (stubble, vehicles, industry, dust, residential)
- **Actionable alert system**: "Ward X will reach AQI 350+ tomorrow at 4 PM due to stubble plume from Punjab — recommend school closures and construction ban"
- **Public dashboard**: Ward-level maps with forecast overlays, health advisory, and intervention recommendations
- **Government API**: Structured forecast data for city corporations to integrate into their own systems

**MVP time estimate**: 10-14 weeks

## Stakeholders & Users

- **1.67M** annual deaths attributable to air pollution in India
- **300+** million people living in India's most polluted cities (Delhi NCR, Kanpur, Patna, Lucknow, etc.)
- **City corporations** in 100+ non-attainment cities (National Clean Air Programme)
- **CPCB and State Pollution Control Boards** — regulatory monitoring mandate
- **SAFAR / MoES** — operational forecasting
- **Citizen groups and health researchers** — exposure assessment and advocacy

## Data Sources

| Source | Description |
|--------|-------------|
| [CPCB CAAQMS](https://app.cpcbccr.com/ccr/#/caaqm-dashboard-all/caaqm-landing) | 300+ real-time air quality monitoring stations (hourly PM2.5, PM10, NOx, SO2, O3, CO) |
| [SAFAR](https://safar.tropmet.res.in/) | Air quality forecasts for 10 Indian cities (seasonal) |
| [MODIS MAIAC](https://lpdaac.usgs.gov/products/mcd19a2v061/) | Aerosol Optical Depth at 1km resolution (daily) |
| [Sentinel-5P](https://sentinels.copernicus.eu/web/sentinel/missions/sentinel-5p) | NO2, SO2, CO, HCHO column concentrations (urban scale) |
| [ERA5](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels) | Hourly meteorological fields (wind, temperature, PBL height, humidity) |
| [IMD Gridded Data](https://mausam.imd.gov.in/) | District-level weather forecasts and rainfall |
| [OpenAQ](https://openaq.org/) | Global aggregator of air quality data (includes CPCB feeds) |

## Key Papers

1. GBD MAPS Working Group (2024). *Burden of Disease Attributable to Air Pollution in India*. Lancet Planetary Health.
2. Dey, S. et al. (2023). *Satellite-based air quality monitoring in India: progress and gaps*. Current Science.
3. Central Pollution Control Board (2024). *National Air Quality Index: Methodology and Implementation*. MoEFCC.
4. Guttikunda, S. & Jawahar, P. (2023). *Source apportionment of PM2.5 in Indian cities*. Urban Emissions.
5. NASA ARSET (2022). *Satellite Remote Sensing for Air Quality Monitoring*.

## Open Source Adjacencies

- [OpenAQ](https://openaq.org/) — Open aggregator of air quality data (Python SDK available)
- [NASA Giovanni](https://giovanni.gsfc.nasa.gov/) — Satellite data exploration (no API for automated pipeline)
- [Google Earth Engine](https://earthengine.google.com/) — Satellite data processing platform (free for research)
- [UrbanEmissions.info](https://urbanemissions.info/) — India-specific emission inventories and source profiles
- [CPCB Central Control Room](https://app.cpcbccr.com/) — Real-time data API (undocumented but scrapeable)

## Success Criteria

- [ ] Ward-level AQI nowcast within ±15% of nearest monitor reading
- [ ] 48-hour forecast within ±25% MAE at city scale
- [ ] Source apportionment identifies stubble burning events with >80% precision
- [ ] Pipeline runs entirely on free/open data (no paid API keys)
- [ ] Dashboard deployed for at least 3 pilot cities (Delhi, Bengaluru, Patna)
- [ ] City corporation pilot partner confirmed for ground-truth validation

## Skills Needed

- Python (pandas, xarray, scikit-learn, LightGBM)
- Remote sensing (MODIS, Sentinel-5P data processing, GDAL)
- Time-series ML (LSTM, ensembles, Prophet)
- Geospatial analysis (GeoPandas, rasterio, Google Earth Engine)
- Web dashboard (Streamlit/React + mapbox/leaflet)
- API integration (CPCB, IMD, OpenAQ)

## Risks

| Risk | Mitigation |
|------|------------|
| CPCB data has gaps and inconsistencies | Multiple monitor fusion + satellite gap-filling; explicit data quality flags |
| Satellite AOD has cloud coverage limitations | Ensemble with chemical transport model (MERRA-2) and in-situ data |
| Source apportionment requires local emission inventories | Use open inventory (UrbanEmissions.info, EDGAR) + satellite constraints |
| City corporation adoption depends on political will | Build public-facing value first; city dashboards are secondary |
| Forecast accuracy degrades during extreme events (Diwali, stubble season) | Ensemble model with scenario-specific calibration |
