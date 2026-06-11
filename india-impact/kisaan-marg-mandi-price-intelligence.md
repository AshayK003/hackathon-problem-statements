---
track: india-impact
status: published
---

# Kisaan Marg — Mandi Price Intelligence

> "Farmers receive only 35–40% of the final consumer price. Intermediaries capture the rest. No advisory layer exists on top of Agmarknet's 3,000+ mandi prices to tell a farmer where to sell, when to hold, or what to grow."

## The Problem

India has 146 million farm holdings, 86% of which are small and marginal (less than 2 hectares). These farmers operate with razor-thin margins and face a persistent structural problem: they capture only 35-40% of the price consumers pay. The remaining 60-65% is captured by intermediaries — aggregators, wholesalers, commission agents, and retailers who control market access and price information.

The government's Agmarknet portal publishes daily prices from over 3,000 regulated mandis across the country. This is a rich dataset covering commodities, varieties, minimum/maximum/modal prices, and arrival quantities. But it is published as raw, tabular data with no interpretation, no forecasting, and no personalised advisory layer. A farmer in a village 50 km from the nearest mandi has no easy way to know that "Market A is paying ₹12/kg more than Market B today" or that "prices for tomato are expected to rise next week — consider holding."

This information asymmetry is not a technical problem — it is a missing AI layer. The data exists, the API is free, and the stakeholders are quantified. What does not exist is a voice-first, multi-lingual, intelligent agent that converts raw mandi prices into actionable decisions for the individual farmer.

## Why Existing Solutions Fail

| Approach | Limitation |
|----------|-----------|
| Agmarknet portal | Raw tabular data; no interpretation, alerts, or forecasting |
| MandiBhavIndia | Price display only; no intelligence or personalised advice |
| WhatsApp price groups | Manual, non-scalable, noisy, limited to specific communities |
| Kisan Suvidha app | General information app; no predictive or arbitrage intelligence |
| Farmonaut / Ninjacart | B2B supply-chain platforms; not farmer-facing or advisory |
| Kisan Call Centre | Reactive voice helpline; no proactive or automated advisory |

## What to Build

- **Price forecasting model**: Time-series ML that predicts mandi prices 7-14 days ahead for major commodities
- **Market arbitrage detector**: "Market A is ₹12/kg more than Market B" — factoring in transport cost and time
- **Sell / hold / transport advice**: Personalised recommendation based on current price, forecast trend, and distance
- **Crop planning assistant**: "Based on last 3 years of price data, the best window to plant arhar in this district is..."
- **Bargaining assistant**: Farmer inputs local trader's offer → agent replies with mandi price + fair range + talking points
- **Multi-lingual, voice-first interface**: Hindi + 8 regional languages, WhatsApp/SMS input, voice replies
- **Daily SMS price alert**: Farmer texts "tomato" → receives best mandi price within 50 km, trend, and recommendation

**MVP time estimate**: 10-12 weeks

## Stakeholders & Users

- **146M** farm holdings (86% small/marginal)
- **~600M** people directly or indirectly dependent on agriculture
- **3,000+** regulated mandis covered by Agmarknet
- **15,000+** traders and commission agents
- **10,000+** Farmer Producer Organisations (FPOs)

## Data Sources

| Source | Description |
|--------|-------------|
| [Agmarknet API](https://agmarknet.gov.in/) | Daily mandi prices for 3,000+ markets (free, data.gov.in) |
| [IMD Weather API](https://mausam.imd.gov.in/) | District-level weather forecasts for crop advisory |
| [CACP Price Policy Reports](https://cacp.dacnet.nic.in/) | Annual price policy reports and MSP recommendations |
| [CSP / Kisan Credit Card data](https://www.nabard.org/) | Farmer credit and crop pattern data (aggregate) |

## Key Papers

1. Chand, R. & Singh, J. (2023). *Market Integration and Price Transmission in Indian Agricultural Markets*. Indian Journal of Agricultural Economics.
2. NITI Aayog (2023). *Doubling Farmers' Income: Report of the Committee*. Government of India.
3. World Bank (2021). *India: Agricultural Markets and Farmer Welfare*. World Bank Group.
4. CACP (2025). *Price Policy for Kharif/SRabi Crops*. Commission for Agricultural Costs and Prices.
5. Gulati, A. et al. (2023). *Transforming Indian Agriculture Value Chains*. ICRIER Working Paper.

## Open Source Adjacencies

- [CEDA Agri Market Data](https://ceda.ashoka.edu.in/) — Ashoka University's agricultural market dataset
- [Farmonaut API](https://www.farmonaut.com/) — Satellite-based crop monitoring (B2B, but has API)
- [Open Food Facts India](https://in.openfoodfacts.org/) — Open food product database

## Success Criteria

- [ ] Cover 3 states / 50 mandis in initial pilot
- [ ] Price forecast within 15% accuracy for 7-day window
- [ ] < 2 second WhatsApp response time for price queries
- [ ] 100 farmers actively using in pilot (self-reported WhatsApp interactions)

## Skills Needed

- Agmarknet API integration and data pipeline
- Basic ML / time-series forecasting (Prophet, LSTM, or LightGBM)
- LLM for conversational interface and regional language support
- WhatsApp Business API / Twilio integration
- Hindi + 8 regional language NLP (speech-to-text, text-to-speech)
- React Native / mobile-first development

## Risks

- Low smartphone adoption among older farmers — must be voice-first and SMS-capable
- Traders and intermediaries may oppose price transparency initiatives
- Agmarknet data quality issues (missing entries, delayed updates, inconsistent formats)
- Language diversity requires multi-lingual support beyond Hindi (8+ languages in MVP states)
- Digital literacy levels vary widely — UX must be ultra-simple
