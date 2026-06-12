---
track: frontier-platforms
status: published
---

# Frontier 07 — Food Waste Surplus Redistribution & Logistics Optimization

> 1.05B tonnes of food wasted (19% of consumption) while 733M face hunger. Food waste = 8-10% of global GHG. No open-source platform combines surplus prediction, perishable-goods routing, and donor-recipient matching.

## The Problem

$940B-$1T annual global economic cost. 45 trillion gallons of water (1/4 of ag water) used for food never eaten. Food is #1 landfill material (22% of MSW), producing methane 80x more potent than CO₂. Existing redistribution is reactive, volunteer-dependent, and lacks predictive analytics. No system predicts surplus before it happens, optimizes collection routes with perishability constraints, and matches food types to recipient demand.

## Why Existing Solutions Fail

| Solution | Limitation |
|----------|-----------|
| **Too Good To Go** | Consumer surprise bags only; no upstream; no prediction |
| **Olio** | Peer-to-peer; volunteer-dependent; no routing |
| **Food Rescue US** | Manual matching; no ML prediction |
| **FoodCloud** | Physical hub; Ireland/UK only |
| **Feeding America MealConnect** | Basic; no forecasting or routing |
| **Afresh** | Grocery ordering optimization only; closed-source |

## What to Build

- Surplus prediction engine (Prophet/LightGBM) — POS data + weather + seasonality + promotions
- Multi-depot VRP optimizer with time windows, split pickup/delivery, perishability decay
- Bipartite matching — surplus food type/qty/shelf-life to recipient demand
- Dynamic pricing optimizer for retail surplus markdowns
- Impact analytics — tonnage rescued, meals provided, GHG avoided

**MVP (3-4 months solo):** Surplus prediction model (open retail data) → OR-Tools VRP solver → matching engine → food bank pilot

## Stakeholders

- 60M+ grocery/food retail establishments globally
- 200+ food banks in Feeding America (60K agencies)
- 733M food-insecure people
- Every farm, manufacturer, distributor, restaurant

## Data Sources

| Source | Description |
|--------|-------------|
| FAO Food Loss & Waste Database | 29K+ data points, global |
| UNEP Food Waste Index Report | 93 countries |
| USDA ERS LAFA | 200+ commodities, US |
| EPA WARM (v16) | GHG emissions calculator |
| ReFED Insights Engine | US food waste + financial data |

## Key Papers

- Dubey & Tanksale (2022) — "Multi-Depot VRP with Split Pickup/Split Delivery for Surplus Food Recovery" — IIT BHU
- Game Theoretic Framework for Surplus Food (2021) — *Applied Sciences* (MDPI)
- Optimization Models for Food Supply Chains Review (2024) — *ICMSIE*
- ReFED AI Report (2026) — "The Food Operating System: How AI Reduces Food Waste"

## Open Source Adjacencies

- [Sharing Excess](https://github.com/sharingexcess) — React PWA food rescue
- [OSRM](https://github.com/Project-OSRM/osrm-backend) — Open Source Routing Machine
- [Food-Waste-Reduction-and-Redistribution-System](https://github.com/food-waste) — Surplus prediction + matching

## Skills Needed

- Operations research (VRP, OR-Tools)
- Time series ML (Prophet, LightGBM)
- React + FastAPI
- GIS/mapping (MapLibre GL)
- Supply chain logistics knowledge

## Risks

- Cold chain perishability — temperature data required for accuracy
- Volunteer reliability — last-mile delivery depends on human availability
- Food poisoning liability from near-expiry redistribution
- Retailers don't share POS data freely — partnerships needed
- Afresh raised $200M+; well-funded competition in prediction space
