---
track: rapid-prototype
status: published
---

# Informal Worker Skills Passport

> **Category:** Labor | Livelihoods
> **Build time:** 4–6 weeks (solo developer)

## The Problem

There are 15–20 million informal waste workers (pickers, sorters, recyclers) worldwide — plus tens of millions more in domestic work, construction, and street vending. These workers have no formal employment contract, no work history, no references, and no way to prove their skills to an employer or a cooperative.

When a waste picker wants to join a formal recycling facility, transition to a better-paying role, or apply for a government ID program, there is nothing to show but their word. Employers have no way to verify experience, skills, or reliability. The result is that informal workers are trapped in the most precarious, lowest-paying segment of the labor market — not because they lack skills, but because they lack the documentation to prove them.

Existing digital identity solutions (Aadhaar in India, MOSIP in Kenya) solve for *who you are*, not *what you can do*.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| Word of mouth / personal references | Unverifiable; doesn't transfer across cities |
| Employer's private notebook | Lost when the middleman changes jobs; no worker ownership |
| Government ID systems (Aadhaar, NIDA) | Identity only; no work history or skills data |
| Paper certificates from informal training | Easily forged; no verification; often not recognized by employers |
| Nothing | Default for 90%+ of informal workers |

## What to Build

An **offline-first mobile app** for informal workers to build and own their work profile. Self-sovereign — the worker controls what goes in, who sees it, and when to share it.

**Worker profile:**
- Photo + name + location (city / area)
- Bio: years of experience, work types, languages spoken
- Work history: employer name, role, duration, tasks — peer-verified (co-worker attests)
- Skills: demonstrated through in-app assessments (e.g., "sort 5 material types in 60 seconds" for a waste sorter)
- Employer references: QR-scannable verification from past buyers or supervisors
- QR code export: full profile encoded as a signed QR that employers can scan with any phone

**Verification model:**
- Peer verification: a co-worker attests that you worked at a certain site
- In-app assessments: timed, skill-specific challenges recorded locally
- Employer stamp: employer scans worker's QR, enters a rating + verification code
- Ed25519 signing: each profile entry is cryptographically signed to prevent tampering

**Offline-first:**
- Full app functionality without internet
- SQLite for local storage; Supabase sync when online
- QR generation/scanning works offline
- Profile PDF (for print) generated on-device

**No AI.** Pure cryptographic verification + structured data + QR codes.

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Mobile framework | React Native (Expo) | Cross-platform; offline-first with SQLite |
| Local database | SQLite (via expo-sqlite) | Works entirely offline; syncs when connected |
| Cloud sync | Supabase (Postgres + auth + storage) | Generous free tier; real-time sync; row-level security |
| Cryptography | TweetNaCl (ed25519 signing) | Lightweight key pair signing for profile integrity |
| QR | react-native-qrcode-svg + expo-camera | Generate and scan QR codes offline |
| Maps (optional) | react-native-maps | Show nearby workers and employers |
| Deployment | EAS Build (Expo) + Supabase | One-command deploys to both stores |

## Stakeholders

- **15–20 million informal waste workers** globally (primary user base)
- **WIEGO** (Women in Informal Employment: Globalizing and Organizing) — global network of informal worker organizations
- **GIZ, ILO, UNDP** — labor and livelihoods programs
- **Ethical employers** — recycling facilities, construction firms, cleaning services that want verified workers
- **Fair-trade certifications** (Fair Trade USA, Fair for Life)
- **Government social protection programs** needing verified work data

## Why This Is Hackathon-Sized (for an experienced mobile dev)

- **No AI, no real-time networking** — the hard parts are offline storage and QR crypto, both well-documented libraries
- **Offline-first is a solved pattern** — SQLite + sync has countless open-source examples
- **Ed25519 signing** is a few lines of code with TweetNaCl
- **The QR flow** is camera → decode → verify → display; a well-trodden path
- **Single-user model** — each instance is one worker's passport; no multi-tenant social network complexity
- **MVP is a static profile app** — assessments, peer verification, and employer stamps can be incremental

**Build time note:** 4–6 weeks is realistic because the core (profile + QR + offline) can be done in 2–3 weeks; verification features are additive.

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | App scaffold + offline profile | React Native project setup; SQLite schema; photo + bio fields |
| Week 2 | QR generation + scanning | Generate signed QR code; scan + verify on another device |
| Week 3 | Work history + peer verification | Add work entries; peer claim-attest flow via QR share |
| Week 4 | In-app skills assessments | Timed skill challenges (e.g., sorting, counting, safety Q&A) |
| Week 5 | Employer stamp + Supabase sync | Employer QR verification; background sync when online |
| Week 6 | Polish and store submission | Profile PDF export; multi-language (English + 1 local); app store submission |

## Monetization

| Model | Details |
|---|---|
| B2B verification fee | $2–$5 per employer verification check (employer scans QR to verify a worker) |
| Enterprise bulk verification | $10K–$50K/year for ethical employers who need to screen 1,000+ workers |
| NGO program integration | GIZ, ILO, UNDP contracts for deployments with target worker groups ($50K–$200K) |
| Freemium app | Free for workers; paid employer dashboard with bulk search + verification log |

**Target:** 10,000 workers onboarded via WIEGO partner organizations in year one.

## Long-Term Vision

A decentralized reputation network for the global informal economy. Workers carry their passport across cities and countries. Employers build trust through verified hiring history. Governments use passport data for social protection targeting. The QR code becomes the informal worker's resume, reference, and ID all in one — owned by the worker, verified by the community, trusted by employers.

## Risks

| Risk | Mitigation |
|---|---|
| Worker smartphone penetration | Target Android Go / low-end devices (React Native supports API 24+); QR export works from feature phones with a camera |
| Low digital literacy | Partner with WIEGO for training; design for icon-driven navigation |
| Verification fraud / collusion | Ed25519 signatures prevent tampering; randomization in assessments; employer stamps cost money (deters spam) |
| Worker data security / privacy | Profiles are held on-device; Supabase RLS restricts cloud access; worker deletes data at any time |
| Employer adoption | Start with WIEGO-affiliated ethical employers; free verification for first 1,000 checks |
