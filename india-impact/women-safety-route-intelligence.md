---
track: india-impact
status: published
---

# Women Safety Route Intelligence

> Over 50% of Indian women report having their mobility restricted due to safety concerns. Street harassment and the fear of assault create an invisible geography of avoidance — yet no routing engine accounts for it.

## The Problem

Women in Indian cities navigate a hidden geography. Streets that are safe at noon become dangerous at 9 PM. A route well-lit and populated on one block turns dark and deserted around the corner. The National Crime Records Bureau (NCRB) consistently reports over 30,000 cases of rape and 300,000+ cases of assault against women annually — but these are reported incidents. Surveys like the ICRW's Safe Cities study suggest the actual prevalence of street harassment is far higher, with over 50% of women in major Indian cities reporting daily or weekly experiences of harassment that affect their mobility choices.

The result is a mobility tax: women spend more time, money, and cognitive effort planning routes that avoid unsafe areas. They take longer paths, use more expensive transport, avoid evening activities, and forgo economic opportunities. This is not a solved problem. Navigation apps (Google Maps, Maps.me, OSMAnd) optimise for shortest/fastest, not safest. Safety information — when it exists — is static, aggregated, and outdated. Safetipin crowdsources safety audits but produces static score maps, not dynamic routing. No open platform ingests crime data, street infrastructure, lighting, and temporal patterns to compute real-time safest routes.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| Google Maps / OSMAnd | Optimise for time/distance; no safety dimension in routing |
| Safetipin | Read-only safety score map; no routing; sparse audit coverage |
| NCRB crime statistics | Annual aggregate reports; not usable for real-time routing |
| Navi.io (academic prototype) | Research prototype; not deployed or maintained |
| Safe Route AI (blog concept) | No working code or public platform |
| City SafeCity dashboards | Static maps; no API; no routing integration |

## What to Build

- **Safety score layer**: ML model that predicts per-street safety score at hourly resolution using crime data (NCRB, state police), street infrastructure (lighting from OSM, police station distance), crowdsourced incident reports, and temporal patterns
- **Safety-aware routing engine**: Modified OSRM or GraphHopper that optimises for safety-time Pareto frontier (safest route within X% time penalty)
- **Crowdsourced incident reporter**: WhatsApp/SMS bot allowing users to anonymously report harassment spots (with photo, time, and description — moderated before public release)
- **Trip planning mode**: "I need to go from A to B, arriving at 9 PM — show me the safest route within 15 extra minutes"
- **Community heat map**: Visualisation of high-risk areas by time of day, aggregated and anonymised
- **Alert zone boundaries**: Geofence-triggered alerts when entering historically unsafe zones at unsafe hours
- **Privacy-first architecture**: All location data stays on-device; no tracking of individual users; reports are anonymised

**MVP time estimate**: 8-12 weeks

## Stakeholders & Users

- **50%+** of Indian women who modify their travel due to safety concerns
- **~25 million** women commuting daily in top 10 Indian cities
- **City police departments** — NCRB reporting mandate, patrol planning
- **Urban local bodies** — street lighting and infrastructure planning
- **Women's safety NGOs** (Jagori, Breakthrough, Safetipin)
- **Transit authorities** — last-mile connectivity planning for women

## Data Sources

| Source | Description |
|--------|-------------|
| [NCRB Crime Statistics](https://ncrb.gov.in/) | Annual district-level crime against women data |
| [OpenStreetMap](https://www.openstreetmap.org/) | Street network, lighting, police stations, land use (via OSMnx) |
| [Safetipin](https://safetipin.com/) | Crowdsourced safety audit data (partner access) |
| [SafeCity Delhi](https://safecity.in/) | Crowdsourced street harassment reports (API available for research) |
| [Google POI / Places](https://developers.google.com/maps/documentation/places/web-service/overview) | Business density as proxy for pedestrian activity |
| [Nighttime Lights (VIIRS)](https://eogdata.mines.edu/products/vnl/) | Satellite-derived illumination proxy for street lighting |

## Key Papers

1. Viswanath, K. & Basu, A. (2023). *Safetipin: Using data to create safe public spaces for women*. ICRW.
2. ADB (2022). *Using Data to Improve Women's Safety in Cities and Transport*. Asian Development Bank Blog.
3. NCRB (2024). *Crime in India: Annual Report*. National Crime Records Bureau.
4. CHI (2023). *Crowdsourcing Data for Safer Travel Experiences for Women in India*. ACM CHI.
5. World Bank (2022). *Handbook for Gender-Inclusive Urban Planning and Design*.

## Open Source Adjacencies

- [OSRM](https://github.com/Project-OSRM/osrm-backend) — Open-source routing engine (can be modified for custom cost functions)
- [OSMnx](https://github.com/gboeing/osmnx) — Download OSM street networks with infrastructure metadata
- [Leaflet](https://leafletjs.com/) — Mobile-friendly map visualisation
- [GraphHopper](https://github.com/graphhopper/graphhopper) — Alternative routing engine with custom weighting support
- [Safetipin open data](https://safetipin.com/) — Partner with them for audit data

## Success Criteria

- [ ] Safety score model achieves AUC > 0.75 against crowdsourced incident validation data
- [ ] Routing engine computes safety-time Pareto routes for a 10km city trip in < 5 seconds
- [ ] Crowdsourced reporter handles 100+ submissions/day with < 30min moderation turnaround
- [ ] Privacy architecture reviewed: zero user location tracking, encrypted reports
- [ ] Deployed for 1 pilot city (Delhi or Bengaluru) with 100+ beta users
- [ ] NGO partner confirmed for community outreach and ground-truth validation

## Skills Needed

- Python (ML, geospatial, routing)
- ML / classification (LightGBM, XGBoost for safety prediction)
- Geospatial analysis (GeoPandas, OSMnx, shapely)
- Routing engine (OSRM or GraphHopper custom profiles)
- Mobile frontend (React Native / Flutter)
- WhatsApp / Twilio integration for incident reporting

## Risks

| Risk | Mitigation |
|------|------------|
| Crime data is reported at district/police-station level, not street level | Downscale using street infrastructure features + land use + crowdsourced reports |
| Crowdsourced reports may have biases (over-reporting in wealthier areas) | Normalise by pedestrian volume; cross-validate with police and audit data |
| Privacy concerns around route tracking | All computation on-device; server receives only anonymised aggregate reports |
| Low initial adoption | Partner with women's hostels, colleges, and corporate commuter programs |
| Reinforcing avoidance (showing unsafe areas may increase fear) | Frame as empowerment: "here is the safest way" not "here are dangerous areas" — always provide routing alternative |
