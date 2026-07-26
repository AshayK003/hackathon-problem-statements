---
track: india-impact
status: published
---

# Public Transit Optimisation for Indian Cities

> Indian cities carry 70 million+ daily bus trips across 200+ municipal fleets. Less than 5% have real-time GPS tracking. There is no GTFS-based route optimisation platform for the world's most transit-dependent population.

## The Problem

India's public bus system moves over 70 million people daily across more than 200 city fleets. It is the primary mode of transport for the urban poor, carrying most of the city's workforce from peripheries to employment centres. Yet it operates with roughly the same route planning technology it had in the 1980s: fixed routes designed decades ago, static timetables that ignore actual road conditions, and zero real-time information for waiting passengers.

The Government of India's recent bus procurement push (FAME II, PM-eBus Sewa) has put thousands of new buses on the road, but these buses run on old routes with old schedules. A 2023 study by the Institute for Transport and Development Policy (ITDP) found that in Bengaluru, bus occupancy varies from 180% (crush load) to 30% (empty) on different segments of the same route. The data to fix this — GPS pings, ticketing counts, road speeds — exists in silos across city transport corporations, but no open-source tool integrates it into actionable route optimisation.

The challenge is fundamentally different from Western transit systems, where agencies publish General Transit Feed Specification (GTFS) data as a standard. Indian city buses largely do not. Even where GTFS exists (a handful of metro systems), it is static and not integrated with bus operations. What is needed is an open platform that builds GTFS from whatever data is available — manual surveys, crowdcourced timings, GPS from onboard devices — and uses it to optimise routes, frequencies, and crew allocation.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| City transport corporation timetables | Static paper schedules; no real-time adjustment; based on decade-old route surveys |
| Google Transit | Works only with official GTFS feeds; < 5% of Indian city buses are covered |
| Chalo / Tummoc | Real-time bus tracking apps for select cities; closed platforms; no route optimisation |
| ITDP / WRI studies | Academic recommendations; no operational software |
| MoRTH / UITP reports | High-level policy; no city-level actionable data |
| OSM-based transit mapping (OpenRouteService) | No real-time integration; no Indian-specific calibration |

## What to Build

- **GTFS importer and QA tool**: Ingest whatever data exists (GPS logs, ticketing, manual survey, paper timetables) and produce standard GTFS feeds with quality metrics (coverage %, schedule deviation, gap identification)
- **Route performance monitor**: Per-route, per-segment occupancy, speed, headway variability, and bunching detection using available GPS and ticketing data
- **Frequency optimiser**: Recommend frequency adjustments based on time-of-day demand patterns extracted from ticketing and crowd-sourced occupancy
- **Route redesign assistant**: "Segment X consistently runs at 160% occupancy during peak hours and 40% during off-peak — recommend (a) adding express service or (b) splitting the route"
- **Passenger-facing ETA**: Real-time bus arrival estimates built from crowd-sourced location (opt-in from app users) fused with whatever GPS data is available
- **Crew scheduling helper**: Optimise shift allocation based on recommended frequencies and driver duty hour regulations

**MVP time estimate**: 12-16 weeks

## Stakeholders & Users

- **70M+** daily bus riders across Indian cities
- **200+** city/state transport corporations (STUs)
- **~2.5 lakh** public bus drivers and conductors
- **NITI Aayog** — PM-eBus Sewa scheme monitoring
- **ITDP, WRI India, EMBARQ** — sustainable urban mobility research
- **Chalo, Tummoc, and other mobility apps** — potential data partners

## Data Sources

| Source | Description |
|--------|-------------|
| City transport corporation GPS feeds | Real-time bus location where available (fragmented, non-standard) |
| UTS mobile ticketing | IRCTC's suburban ticketing app (train + some bus, aggregate volume data) |
| OpenStreetMap | Road network, bus stops (crowdsourced, improving coverage) |
| Google Maps PTR (limited) | Public transit routes for select cities (not downloadable programmatically) |
| MoRTH road accident data | Black spot identification for route safety audits |
| India Census (2011) + Census 2024 projections | Ward-level population density and commute pattern estimates |

## Key Papers

1. ITDP (2023). *Bus Karo: A Guide to Improving Bus Systems in Indian Cities*. Institute for Transport and Development Policy.
2. WRI India (2024). *Data-driven public transport planning in Indian cities: challenges and opportunities*.
3. MoRTH (2023). *Urban Bus Specification II and PM-eBus Sewa Scheme*. Ministry of Road Transport and Highways.
4. Shakti Foundation (2023). *State of Public Transport in Indian Cities*.
5. Changing Transport (2021). *Roadmap for Data-driven Transformation of Indian Bus Systems*.

## Open Source Adjacencies

- [OpenTripPlanner](https://www.opentripplanner.org/) — Open-source multimodal trip planner (GTFS-based)
- [GTFS.org](https://gtfs.org/) — GTFS standard and validator tools
- [OSMnx / OSM](https://github.com/gboeing/osmnx) — Street network and transit stop extraction
- [MobilityData/awesome-transit](https://github.com/MobilityData/awesome-transit) — Community transit tools catalogue
- [OpenRouteService](https://openrouteservice.org/) — Route optimisation with custom profiles

## Success Criteria

- [ ] GTFS importer produces valid GTFS feed from at least 3 different data source types (GPS, ticketing, manual)
- [ ] Route performance monitor identifies 5+ actionable optimisation opportunities per route (e.g., "reduce frequency 15% on segment X during Y hours")
- [ ] Frequency optimiser reduces headway variance by 20% in simulation using 1 city's data
- [ ] ETA accuracy within ±3 minutes for routes with at least 50% GPS coverage
- [ ] Open-source release: all code under MIT license
- [ ] Pilot partnership with at least 1 city transport corporation

## Skills Needed

- Python (data pipeline, GTFS processing, optimisation)
- GTFS data model and validation (transitfeeds-python, gtfs-lib)
- Operations research / optimisation (linear programming, constraint solving)
- Geospatial (GeoPandas, shapely, routing basics)
- Web frontend (dashboard + map visualisation)
- Partnership and stakeholder management (STU coordination)

## Risks

| Risk | Mitigation |
|------|------------|
| Transport corporations reluctant to share operational data | Start with crowdsourced data + open OSM routes; prove value before requesting sensitive GPS data |
| GPS data, if available, is in non-standard formats | Build flexible parsers with schema mapping per corporation |
| Indian cities lack standard GTFS — most have no structured transit data | Build workflows to create GTFS from surveys and crowdsourced timing |
| Bunching and reliability issues are structural (traffic, driver shortage), not just algorithmic | Clearly scope what routing changes can fix; recommend complementary policy interventions |
| No bus stop data in machine-readable format | Extract stops from OSM + manual survey onboarding interface for field workers |
