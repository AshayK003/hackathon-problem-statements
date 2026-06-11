---
track: rapid-prototype
status: published
---

# Setu — Government Form Assistant

> **Category:** Governance | Citizen Services (India)
> **Build time:** 3–4 weeks (solo developer)

## The Problem

Every Indian citizen regularly needs to fill government forms: caste certificate applications, income certificate requests, birth and death registration, marriage certificate applications, passport applications, PAN card changes, voter ID updates, and a bewildering array of scheme-specific application forms. Each of these forms is different across India's 29 states and 8 Union Territories, typically available only in English or Hindi, and requires a specific set of supporting documents that is never clearly listed in one place.

The result is a deeply frustrating experience that millions of Indians face every single day. A low-income family applying for a caste certificate in rural Maharashtra must figure out which of several online portals to use, which documents to attach, whether to visit the tehsildar office, and how to track their application — all without a single unified guide. Common problems include: forms that do not auto-save, causing hour-long data entry sessions to be lost on page refresh; supporting document requirements that change without notice; and forms that require physical submission despite being available online.

Services like UMANG and DigiLocker have made progress on service discovery and document storage, but neither addresses the core problem: helping an ordinary citizen fill out the right form correctly the first time. The technology is straightforward — guided form workflows, document checklists, and submission tracking are all solved problems. What is missing is a unified, citizen-friendly layer on top of the existing government digital infrastructure.

## Current Solutions and Limitations

| Approach | Limitations |
|---|---|
| State e-District portals | Each state runs its own portal with different UX; most are poorly designed, slow, and not mobile-friendly |
| UMANG app | Comprehensive service catalog but overly complex UI; poor form-filling experience; no auto-fill |
| DigiLocker | Excellent for document storage and verification; does not help with form filling or submission |
| CSC (Common Service Centres) | Human-assisted form filling at ₹10–50 per application; not scalable; no digital record of past submissions |
| Private tax/legal portals | Focused on income tax and business filings; ignore the common citizen's most-needed forms (caste, income, birth, death) |

## What to Build

- **Form finder** — Natural-language query interface: "I need an income certificate in Maharashtra" → returns the exact form, portal link, fee, and processing time
- **Smart form filler** — Step-by-step guided form filling with progress save, input validation, and contextual help in Hindi and English
- **Document checklist generator** — Based on the selected form and user profile (state, category, gender), generate a precise list of required documents with examples
- **DigiLocker prefill** — With user consent, auto-fill name, date of birth, father's name, and address from DigiLocker-stored documents (Aadhaar, PAN, Voter ID)
- **Submission tracker** — Track application status across multiple state portals from a single dashboard with push notifications
- **Template library** — Community-maintained templates for 50+ most common government forms with step-by-step screenshots and video guides
- **Offline kit** — For users without reliable internet: downloadable PDF forms with pre-filled data and a checklist

## Tech Stack

| Component | Choice | Why |
|---|---|---|
| Backend | Python FastAPI | Lightweight, async, excellent for API orchestration (DigiLocker, UMANG, state portals) |
| Database | PostgreSQL + pgvector | Structured form metadata; pgvector for future semantic form search (Phase 2) |
| Frontend | Next.js + Tailwind CSS | SSR for SEO ("how to apply for income certificate in Bihar"); PWA for offline support |
| Forms | React Hook Form + Zod validation | Performant form library with excellent validation support for complex conditional forms |
| APIs | DigiLocker OAuth + Aadhaar eKYC + UMANG | Official government APIs for identity verification and service discovery |
| Deployment | Railway / Vercel | Zero-ops; free tier handles the traffic for an MVP |
| Monitoring | Sentry + Highlight | Track form abandonment and errors to continuously improve the experience |

## Stakeholders

- **Every Indian citizen** — roughly 1 billion+ annual application processes across all form types
- **36 state governments** — each benefits from reduced counter traffic and fewer rejected applications
- **CSC (Common Service Centre) operators** — can use Setu as a digital backend while still providing human assistance
- **Banks, employers, and educational institutions** — as verifiers of caste, income, and other certificates
- **Government departments** — receive better-quality applications with fewer errors, reducing processing time

## Why This Is Hackathon-Sized

- **Form logic is deterministic** — conditional fields, validation rules, and document requirements are simple if-then-else logic
- **DigiLocker API handles identity** — no need to build verification infrastructure; use existing government APIs
- **State forms are structurally similar** — they differ in URLs and field labels, not in fundamental logic; an adapter pattern handles variety
- **No ML needed until Phase 2** — Phase 1 is pure form logic + API integration; semantic search is a future enhancement
- **Templates are community-contributed** — users and contributors add new forms over time without requiring core team effort

## MVP Timeline

| Week | Focus | Deliverable |
|---|---|---|
| Week 1 | Form finder + 20 most common forms with guides | Searchable form catalog with step-by-step guides in Hindi and English |
| Week 2 | Document checklist generator | Context-aware document requirement list for each form variant |
| Week 3 | DigiLocker OAuth + auto-fill | Login via DigiLocker; auto-populate personal details in forms |
| Week 4 | Submission tracker for 3 states (Maharashtra, Karnataka, UP) | Dashboard showing application status across tracked portals |

## Monetization

| Model | Details |
|---|---|
| Free tier | Form finder, checklist generator, and guides are always free |
| Premium download | ₹50–100 per verified document download (certificate copy with digital signature) |
| B2G licensing | ₹10–₹50 lakh per year for customized state-specific deployments with SLA |
| Affiliate | Revenue share with DigiLocker premium services and other government service platforms |
| Bulk access | ₹5–₹20 lakh per year for institutions (banks, universities) that need to verify certificates at scale |

**Target:** Free for individual citizens; paid plans for governments and institutions.

## Long-Term Vision

"ClearTax for government forms" — every Indian citizen uses Setu as the default starting point before any government application. The platform evolves into a comprehensive lifecycle manager: it not only helps you fill the form but also tracks the application, reminds you when the certificate is about to expire, and helps you apply for the next document that becomes available (e.g., after getting a caste certificate, suggests applying for scholarships that require it). Integration with DigiLocker, UMANG, and all 36 state portals makes Setu the universal front-end for Indian government services.

## Risks

| Risk | Mitigation |
|---|---|
| State portals break or change URLs frequently | Graceful fallback to static information with "last verified" date; community reporting of broken links |
| User trust and fear of scams | Transparent government branding; clear disclaimers; never ask for passwords (DigiLocker OAuth only) |
| 200+ form variants across 36 states | Community-contributed templates with moderation; start with the 50 most-requested forms |
| DigiLocker consent friction causes drop-offs | Clear, minimal consent UX; explain why each data point is needed and how it helps |
| Form logic errors could cause application rejection | Thorough testing with real government forms; user-contributed corrections with verification |
