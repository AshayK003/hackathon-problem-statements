---
track: global-south-impact
status: published
---

# AI-Assisted Climate-Resilient Housing Design for Informal Settlements

> Housing | Climate Adaptation — 10–14 month build

## The Problem

Over 1 billion people currently live in informal settlements (slums), a number projected to reach 3 billion by 2050. These homes are self-built using local materials (mud brick, corrugated metal, reclaimed wood, bamboo) with no engineering input, no structural calculations, and no consideration of climate risks. As climate change intensifies, these same communities face rising threats from floods, landslides, extreme heat, and windstorms. A single extreme weather event can destroy decades of informal construction. Residents lack access to architects, engineers, or even basic design guidance. There is zero existing AI-based tool that helps informal builders design climate-resilient housing using local materials, local conditions, and cultural preferences — this is completely novel territory with no prior art.

## Why Existing Solutions Fail

| Solution | Gap |
|---|---|
| Formal architectural / engineering services | Cost $5,000–50,000 per house — far beyond reach of slum residents; concentrated in formal sector |
| Humanitarian shelter kits (UNHCR, IFRC, Build Change) | Post-disaster only; standardized designs that ignore local materials, climate, and cultural preferences |
| Pattern language / design pattern books (e.g., Alexander, 1977) | Static, paper-based; cannot adapt to specific site conditions or local material properties |
| Building codes and guidelines | Developed for formal construction; assume materials and skills unavailable in informal settlements; rarely enforced |
| Community-based building knowledge | Valuable but not climate-adapted for future conditions; built on past experience rather than projected climate risk |
| Parametric / generative design tools (Grasshopper, Rhino) | Require expert operators; $500+/year licenses; 3D modeling skills beyond informal context |
| Prefabricated / container housing solutions | Cost-prohibitive at scale; require heavy transport; culturally inappropriate in many contexts |

## What to Build

- **Generative design engine for local materials** — given a plot footprint, local material availability (mud brick, bamboo, timber, metal, stone, recycled materials), and climate hazards (flood, wind, heat, seismic), generate optimal house designs that maximize resilience while using locally available materials
- **Visual reference generation (Stable Diffusion)** — fine-tune a text-to-image model to produce culturally appropriate visual references of climate-resilient housing that uses local materials, helping residents visualize options before building
- **Rule-based structural checking** — implement simplified structural engineering rules (wall thickness, roof pitch, foundation depth, bracing requirements) for common local material types, checking generated designs for minimum safety requirements
- **Climate risk scoring from satellite** — automatically score a given plot or settlement for flood risk (from FABDEM elevation data + historical flood maps), landslide susceptibility (slope + geology + rainfall), heat island risk, and wind exposure
- **Non-literate mobile user interface** — all information conveyed through icons, pictograms, and local language voice guidance; no text reading required; simple flow: "show me your plot" (GPS + satellite photo) → "what materials do you have?" (icon selection) → "what climate risks concern you?" → "here is a safe house design for you"
- **Local materials database** — crowd-sourced repository of building material properties (strength, durability, cost, thermal performance, environmental impact) for materials commonly used in informal construction across different regions
- **Build step guide** — simple, icon-based step-by-step construction instructions generated for each recommended design, adapted to local construction practices and literacy levels

## Stakeholders

- **1+ billion people currently living in informal settlements** (UN-Habitat estimate), projected to reach 3 billion by 2050
- **500+ city governments** in LMICs struggling with informal settlement upgrading and climate adaptation
- **NGOs and international organizations** (UN-Habitat, Build Change, Habitat for Humanity, Architecture Sans Frontières, UNOPS)
- **Slum dweller federations** (SDI, Shack/Slum Dwellers International, National Slum Dweller Federations in 30+ countries)
- **Local materials suppliers and builders** in the informal construction sector
- **Climate adaptation funders** (Green Climate Fund, Adaptation Fund, World Bank Climate Investment Funds, city climate funds)

## Data Sources

- **World Bank Informal Settlements Database** — country-level and city-level coverage of informal settlement populations and characteristics
- **UN-Habitat Urban Indicators Database** — slum household surveys, housing conditions, basic services coverage
- **OpenStreetMap** — building footprints in informal settlements (growing coverage via HOT OSM tasking)
- **Global Flood Database (Cloud to Street / NASA)** — historical flood extent maps at 30m resolution since 2000
- **NASA SRTM / FABDEM** — 30m global elevation data for flood risk and landslide susceptibility modeling
- **USGS Seismic Hazard Maps** — global earthquake hazard zonation for seismic design consideration
- **ERA5 / CMIP6 Climate Projections** — temperature extremes (for heat-resilient design), precipitation intensity (for flood/rain protection), wind speed (for structural wind load)
- **ESA CCI Land Cover** — land surface characteristics for urban heat island modeling
- **Build Change / Habitat for Humanity design archives** — engineering-approved housing designs for informal construction using local materials

## Key Papers

- UN-Habitat (2020) — "World Cities Report 2020: The Value of Sustainable Urbanization" — definitive estimate of 1B+ in slums, projected to 3B by 2050
- Satterthwaite, D. et al. (2020) — "Building Resilience to Climate Change in Informal Settlements" — comprehensive review of climate vulnerability of informal housing
- Melese, S. et al. (2023) — "Artificial intelligence for housing design in developing countries: a conceptual framework" — one of the few papers explicitly linking AI to informal housing design
- Build Change — "Housing Design Guidelines for Disaster-Resistant Construction" (multiple country-specific volumes) — engineering design rules adapted to local materials and vernacular construction
- Echendu, A. (2022) — "Climate change and informal settlements: a review of vulnerability and adaptation options"
- United Nations (2023) — "SDG 11 Progress Report: Making Cities and Human Settlements Inclusive, Safe, Resilient and Sustainable"

## Open Source Adjacencies

- **WikiHouse** — open-source building system for CNC-cut plywood houses (methods adaptable to local materials)
- **OpenStreetMap** — building data, road networks, and humanitarian mapping for settlement-scale analysis
- **Ladybug Tools** — open-source environmental analysis for building design (solar radiation, thermal comfort, wind); adaptable for LMIC materials
- **Stable Diffusion (CompVis / Stability AI)** — open-source text-to-image generation for visual reference creation
- **FABDEM (Fathom / University of Bristol)** — global 30m elevation model removing building/forest bias, superior for flood risk mapping
- **Grasshopper / Rhino Compute (McNeel)** — accessible parametric geometry; Rhino Compute allows server-side deployment without desktop Rhino
- **Blender** — open-source 3D modeling for rendering generated designs
- **HuggingFace Diffusers** — model fine-tuning infrastructure for design reference generation

## Success Criteria

- [ ] Generative design engine produces ≥ 5 structurally viable housing designs per input (plot + materials + hazards) that satisfy rule-based structural checks
- [ ] Stable Diffusion fine-tune generates culturally appropriate, realistic reference images rated ≥ 4/5 by target community members in user testing
- [ ] Climate risk scoring identifies flood/landslide/heat/wind risk with ≥ 85% accuracy validated against known disaster damage data for ≥ 3 pilot settlements
- [ ] Non-literate UI tested with ≥ 20 informal settlement residents (≤ 2 years of schooling) — ≥ 80% can complete the design flow independently
- [ ] Local materials database includes ≥ 30 material types with engineering properties validated by structural engineer
- [ ] Step-by-step build guide is comprehensible by local builders: test with ≥ 10 informal builders, ≥ 90% can follow first 10 steps correctly
- [ ] Full platform deployed and tested in ≥ 2 informal settlements in different countries/climates

## Skills Needed

- 1× ML Engineer (generative design, diffusion models, rule-based geometry generation, physics-informed design constraints)
- 1× Computer Vision / ML Engineer (Stable Diffusion fine-tuning, text-to-image generation, visual quality assessment)
- 1× Full-Stack Developer (mobile app for low-literacy users, geospatial data integration, satellite image processing)
- 1× Structural Engineer / Architect with Informal Housing Experience (structural principles for local materials, settlement upgrading, Build Change or similar experience)

## Risks

| Risk | Mitigation |
|---|---|
| Generated designs may not be culturally acceptable in diverse informal settlement contexts | Build community co-design into the process; allow local material and aesthetic preferences as input parameters; do field validation in multiple cultural contexts |
| Structural safety of generated designs must be guaranteed — liability risk | Position as "advisory concept design," not "engineering approval"; include prominent disclaimers; use conservative safety factors; designs must pass rule-based check before display |
| Land tenure insecurity — many slum residents cannot build permanent structures | Include "upgradable" design options (incremental housing); provide adaptation guidelines for temporary structures; partner with land rights organizations |
| Informal settlement residents have limited phone access and data | Build for ultra-low-cost Android ($30); full offline mode; icon-based UI tested for low digital literacy; explore SMS/voice-only fallback for basic guidance |
| Satellite-derived building footprints are incomplete in informal settlements | Partner with HOT OSM for field mapping; use field digitization workflow within the app itself; pre-populate with existing OSM data where available |
| Local materials have highly variable engineering properties | Use conservative safety factors (5× recommended by formal standards); group materials into broad types with well-characterized lower bounds; build in material testing guidelines using simple field tests |
| Legal/financial barriers to building even with AI guidance | Integrate links to community savings groups; provide incremental building plans; partner with microfinance housing loan programs (e.g., Habitat for Humanity's MicroBuild Fund) |
