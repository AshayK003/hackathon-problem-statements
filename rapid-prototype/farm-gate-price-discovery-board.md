---
track: rapid-prototype
status: published
---

# Farm-Gate Price Discovery Board

> **Category:** Agriculture | Market Access (India)
> **Build time:** 3–4 weeks (solo developer)

## The Problem

India's 146 million farm holdings — 86% of which are small and marginal — face a persistent price information asymmetry. Farmers bring their produce to the local trader and are offered a price with no reference point. They can accept it or take the perishable produce home. Agmarknet publishes wholesale mandi prices, but the farm-gate price — the actual price the farmer receives at their village — is a black box. Middlemen capture 60-65% of the consumer price, and the lack of transparent farm-gate pricing is a primary mechanism.

The farmer knows what they were offered. They don't know what their neighbour 5 km away was offered for the same quality of produce. They don't know if the trader is offering a fair price relative to the nearest mandi. They don't have a way to broadcast their harvest and let multiple agents bid competitively.

Existing price discovery tools (Agmarknet, mandi boards, WhatsApp groups) cover wholesale mandi prices but not the local farm-gate spot market. The need is for a simple, low-tech, non-AI platform where farmers can anonymously share the prices they're being offered and agents can bid on posted harvest lots.

## Current Solutions and Limitations

| Approach | Limitations |
|----------|-------------|
| Agmarknet portal | Mandi wholesale prices only; not farm-gate; requires internet; not actionable for individual negotiation |
| Local trader offers | Single offer, no comparison; farmer has no bargaining leverage |
| WhatsApp farmer groups | Limited reach; moderated by group admin; prices not structured or searchable |
| Gramhal chatbot | Provides mandi prices but 2-3 days old (as reported by farmers themselves); no bidding |
| Neighbourhood word of mouth | Informal, untimely, limited radius |
| MSP announcements | Only covers notified crops (24 crops); most farmers grow vegetables, fruits, pulses not under MSP |

## What to Build

- **SMS price post**: Farmer sends SMS to a shortcode: "5 quintals, brinjal, ₹400/quintal" → their offer price is published on the board
- **Price board by crop and location**: Searchable board showing latest farm-gate prices for each crop in each taluka — "brinjal in Satara taluka: range ₹380-450/quintal, median ₹410"
- **Agent bid system**: Registered agents can post bids on farmer harvest listings; farmer sees competing offers via SMS
- **Price trend dashboard**: Weekly/seasonal trends for major crops by region — "tomato prices in Kolar have dropped 15% this week, consider holding"
- **Quality disclaimer system**: Farmers self-grade produce (A/B/C) with optional photo upload; helps agents bid with confidence
- **Subscription alerts**: Farmer subscribes to a crop → receives daily SMS: "Today's brinjal range in Satara: ₹380-440 (10 offers)"
- **Mandi price reference**: Alongside farm-gate prices, show nearest mandi wholesale price for comparison

## Tech Stack

| Component | Choice | Why |
|-----------|--------|-----|
| Backend | Python FastAPI | SMS handling, simple CRUD, quick to iterate |
| Database | PostgreSQL | Structured price data; spatial queries for taluka-level grouping |
| SMS | Twilio SMS API (₹0.80/message) or MSG91 (Indian, cheaper at ₹0.25/message) | Cheaper SMS; phone verification via OTP |
| Voice IVR | Knowlarity / Exotel (optional Phase 2) | Voice interface for farmers who can't read SMS |
| Frontend | HTML + Tailwind via Next.js | Desktop board for agents; mobile responsive |
| Hosting | Vercel (frontend) + Railway (backend) | Free tier both; no server management |

## Stakeholders

- **146 million** farm holdings (86% small/marginal, < 2 hectares)
- **~600 million** people dependent on agriculture
- **Local traders and commission agents** in 6,000+ mandis
- **Farmer Producer Organisations (FPOs)** — 10,000+ across India
- **Mandi boards** (APMC — Agricultural Produce Market Committees)
- **Kisan Call Centres** — potential distribution partner

## Why This Is Hackathon-Sized

- **No AI** — pure CRUD + SMS aggregation
- **Text-only interface** — no images, no maps, no real-time collaboration
- **Simple data model** — farmers, crops, prices, locations, agents
- **Proven SMS pattern** — mKisan portal, IFFCO's SMS services are reference implementations
- **Clear incentive** — farmers get better prices, agents get more supply visibility
- **No hardware** — works on any phone with SMS capability (including feature phones)

## MVP Timeline

| Week | Focus | Deliverable |
|------|-------|-------------|
| Week 1 | SMS ingestion + data model | Twilio webhook receives farmer messages; parses crop + qty + price; stores in PostgreSQL |
| Week 2 | Price board web interface | Searchable web board showing prices by crop, taluka, date; agent registration + offer posting |
| Week 3 | Agent bid + notification | Agents bid on farmer listings; farmer notified via SMS with competing offers; farmer accepts |
| Week 4 | Price alerts + mandi reference | Subscription alerts; show nearest mandi wholesale price alongside farm-gate median; pilot in 3 talukas |

## Risks

| Risk | Mitigation |
|------|------------|
| Low adoption among older farmers | Partner with FPOs and Kisan Call Centres for onboarding; SMS is lowest-tech interface |
| Agents may collude to suppress prices | Anonymous posting prevents collusion; farmer sees multiple agent bids |
| Price data quality (fake/misleading posts) | Reputation scoring; phone number verification; moderation of flagged posts |
| SMS costs at scale | Use Indian SMS provider (MSG91: ~₹0.25/message); reverse-billed (farmers send free shortcode, agents pay for subscription) |
| Only works for farmers who can read SMS | Voice IVR as Phase 2; partner with existing farmer helplines for pilot |
