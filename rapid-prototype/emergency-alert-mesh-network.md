---
track: rapid-prototype
status: published
---

# Emergency Alert Mesh Network for Cyclone- and Flood-Prone Coastal Communities

> **Category:** Disaster Management | IoT (India)
> **Build time:** 4–6 weeks (solo developer)

## The Problem

India's coastline stretches 7,516 kilometres, home to over 200 million people who face annual cyclone and flood threats. When Cyclone Fani (2019), Cyclone Amphan (2020), and Cyclone Yaas (2021) struck the Bay of Bengal coast, the most critical failure was not in forecasting — it was in last-mile communication. Cell towers collapsed under wind loads or lost power. Internet connectivity vanished. Communities that had received early warnings from IMD could not receive real-time updates on landfall changes, evacuation routes, or relief distribution.

The existing system relies on a fragile chain: IMD alerts → state disaster management → district collector → tehsildar → local officials → community. Each step relies on phones and internet. When the storm hits, the chain breaks. After the storm passes, communities are cut off for days — unable to report casualties, request supplies, or coordinate rescue.

LoRa (Long Range) radio technology can transmit data 5-15 km per hop using milliwatts of power. A mesh network of solar-powered LoRa nodes, deployed on community buildings, can create an off-grid communication backbone that survives power outages and tower failures. Messages hop node-to-node until they reach a gateway with cellular or satellite uplink. The technology is proven in academic prototypes (Disaster Radio, Project LOCATE, multiple IoT papers) — but there is no production-ready, open-source deployment kit tailored for India's cyclone-prone coastal communities.

## Current Solutions and Limitations

| Approach | Limitations |
|----------|-------------|
| Mobile networks (4G/5G) | Towers fail in high winds; no power backup beyond 2-4 hours |
| Satellite phones | ₹50,000-1,00,000 per unit; limited to trained personnel |
| Ham radio | Requires licensed operators; not scalable to community level |
| IMD alert SMS | One-way broadcast; no return channel for communities |
| Manual messenger systems | Slow, dangerous during active disasters |
| Academic LoRa prototypes (research papers) | Not production-ready; no deployment scripts, hardware list, or iOS/Android apps |

## What to Build

- **Solar-powered LoRa mesh node**: ESP32 or similar LoRa-capable microcontroller + solar panel + battery + waterproof enclosure — complete with parts list, assembly instructions, and firmware
- **Mesh routing firmware**: Self-healing mesh protocol (modified AODV or similar) that routes messages node-to-node; auto-discovers new nodes and routes around failed ones
- **Community alert app**: Mobile app (iOS/Android) that connects to the local LoRa node via Bluetooth/WiFi; displays incoming alerts, allows sending SOS messages with GPS coordinates
- **Dashboard for disaster control room**: Web dashboard showing node health, active alerts, SOS locations, mesh topology (works on whatever internet remains)
- **SMS gateway bridge**: At least one node in each deployment connects to a GSM module for SMS relay to disaster control rooms and family contacts
- **Bidirectional messaging**: Community can both receive alerts AND send situation reports (casualties, needs, safe/damaged areas)

## Tech Stack

| Component | Choice | Why |
|-----------|--------|-----|
| Microcontroller | ESP32 with LoRa module (Heltec, TTGO) | Low cost (₹800-1,500), built-in WiFi/BLE, large community, Arduino IDE compatible |
| Protocol | LoRa (868/915 MHz) | 5-15 km range line-of-sight, sub-1W power, license-free ISM band in India |
| Mesh firmware | Modified Meshtastic / RadioLib | Battle-tested open-source mesh; Raspberry Pi gateway support |
| Mobile app | React Native + Expo | Cross-platform; BLE and location APIs; faster iteration than native |
| Dashboard | Next.js + Leaflet maps | Real-time updates via WebSocket; free hosting on Vercel |
| Hardware cost | < ₹3,000 per node | ₹1,200 (ESP32+LoRa) + ₹800 (solar panel) + ₹500 (battery) + ₹500 (enclosure) |

## Stakeholders

- **200 million** people in India's coastal cyclone/flood-prone areas
- **National Disaster Management Authority (NDMA)** and State Disaster Management Authorities
- **India Meteorological Department (IMD)** — early warning generation
- **Coastal district administrations** (collector offices in Odisha, Andhra, Tamil Nadu, Gujarat, West Bengal)
- **Community-based disaster management committees** (local self-help groups, panchayats)
- **Local NGOs** working on disaster preparedness (Goonj, SEEDS, Sphere India)

## Why This Is Hackathon-Sized

- **No ML/AI** — all logic is deterministic (message routing, sensor sampling, alert forwarding)
- **Well-defined physical form factor** — one node design, fixed BOM, one firmware image
- **Existing open-source building blocks** — Meshtastic, RadioLib, ESP32 ecosystem are mature
- **Clear deployment boundary** — 20-50 nodes per village cluster, not city-scale
- **Hardware is cheap** — < ₹3,000 per node; 20 nodes = one satellite phone cost
- **Proven concept** — multiple academic papers and field tests demonstrate feasibility

## MVP Timeline

| Week | Focus | Deliverable |
|------|-------|-------------|
| Week 1 | Hardware BOM + node firmware | Complete parts list with Indian vendors; ESP32 firmware with basic mesh messaging |
| Week 2 | Mesh routing + gateway | Multi-hop routing works across 3 nodes; gateway node relays messages to cloud dashboard |
| Week 3 | Mobile app (alert display + SOS) | iOS/Android app connects to local node via BLE; shows alerts; sends SOS with location |
| Week 4 | Dashboard + SMS gateway | Web dashboard shows node topology and alerts; SOS triggers SMS to pre-configured numbers |
| Week 5 | Field test + power optimisation | Deploy 5 nodes in a rural cluster; solar power tested through 48h no-sun period |
| Week 6 | Documentation + deployment guide | Full README with parts links, assembly photos, firmware flashing walkthrough, and village deployment playbook |

## Risks

| Risk | Mitigation |
|------|------------|
| LoRa range in dense coastal settlements is lower than theoretical max | Field-test node placement at building-height (rooftops, water towers) to maximise line-of-sight |
| Solar + battery sizing varies by location | Provide sizing calculator based on latitude, monsoon cloud cover, and expected duty cycle |
| Community may not maintain nodes | Train 2-3 local volunteers per village; nodes have LED health indicators for simple diagnostics |
| Government adoption slow despite clear need | Frame as citizen-driven initiative; partner with local NGOs for initial deployment |
| Villagers may not carry smartphones for the companion app | SMS gateway bridge ensures feature phone users still receive alerts; public loudspeaker relay from gateway node |
