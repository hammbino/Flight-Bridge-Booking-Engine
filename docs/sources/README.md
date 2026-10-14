---
title: "Source Digests: Index"
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-13
source_transcripts: all
tags: [sources, index, traceability]
---

# Source Digests

Each file in this folder is an agent-optimized digest of one source conversation. It holds only booking-relevant content. Every point carries its type, speaker, and timestamp, so any claim in `docs/booking-engine/` can be checked against evidence without reading a raw transcript.

Raw transcripts processed before 2026-10-07 are not in this repo. They are in the parent repo: `/Users/jeffrey/Sandbox/Flight-Bridge/Transcripts/`. Some conversations exist there under more than one filename with identical content. Each digest lists all of its aliases in `source_transcripts`.

## How to use

- **Tracing a doc entry:** take the filename in its `Source Transcript(s)` field, find the digest below that lists it as an alias, then search the digest's Points table.
- **Point types:** DECISION, REQUIREMENT, IMPLIED (seems implied, not stated), IDEA, QUESTION, RISK, ASSUMPTION, FACT, CONFLICT. Tags like `[borderline]` mean the point only partly touches booking.

## Source keys

Docs in `docs/booking-engine/` cite sources with a short key plus a timestamp, for example `SV 00:28:50`. The key maps to the digest and to the original filenames here.

| Key | Digest | Original filename(s) |
|-----|--------|----------------------|
| SV | strategic-vision-unified-platform.md | Strategic Vision for a Unified Travel Management Platform; Call with Mauricio-transcript.txt |
| EM | 05-22-email-marketing-tool-selection.md | 05-22 Weekly Meeting Flight-Bridge_ Email Marketing Strategy, Tool Selection, and Monetization-transcript.txt; JeffandMauricio.md.md; email_marketing_strategy_tool_selection_and_monotization |
| FS | 05-22-financial-structure.md | 05-22 Meeting Flight-Bridge_ Financial Structure, Credit Cards, and Payment Processing-transcript.txt; Financial_Structure |
| AV | 05-22-avatar-driven-marketing.md | 05-22 Avatar-Driven Marketing Flight-Bridge_ Shifting from Unstable Revenue to a Predictable Sales Model by Targeting the Economic Buyer-transcript.txt; Avatar-Driven Marketing Flight-Bridge |
| PA | 03-16-premium-adventure-experiences.md | 03-16 From Ideation to Productized Premium Adventure Experiences_ A Decision Framework and Go-To-Market Plan-transcript.txt; Premium Adventure Experiences |
| PP | phase-plan-jeff-mauricio.md | Mauricio and Jeff Phase Plan-transcript.txt |
| R1205 | 12-05-traverse-tech-roadmap.md | 12-05 Strategic Roadmap for Traverse Tech Launch and Growth-transcript.txt |
| M0610 | 06-10-newsletter-tiers-booking-flow.md | 06-10 Weekly Meeting_ Newsletter Content Strategy, Subscription Tiers, and Booking Flow-transcript.txt |
| M0924 | 09-24-tier-launch-booking-roadmap.md | 09-24 Meeting_ Tiered Travel Subscription Launch, Email Campaign, and Booking Engine Roadmap-transcript.txt |
| M1008P | 10-08-arc-transfer-paid-launch.md | 10-08 Planning: FlightBridge ARC Transfer and Paid-deals Launch |
| M1008S | 10-08-ai-agent-arc-strategy.md | 10-08 Meeting: FlightBridge Strategy on AI Agent Development, ARC Approval, and Monetization |
| PARENT | n/a | Parent repo docs or working-session decisions, cited by file and ID (for example `PARENT docs/ai/KNOWN_ISSUES.md`) |

New transcripts get a new key here when their digest is written.

M1008P and M1008S have no per-line timestamps. They are cited by line number in the raw file, for example `M1008P L905`.

## Digests (newest first)

| Digest | Date | Booking relevance | Aliases (original filenames) |
|--------|------|-------------------|------------------------------|
| [10-08-arc-transfer-paid-launch.md](10-08-arc-transfer-paid-launch.md) | 2026-10-08 | High. ARC transfer unblocks the engine; engine on hold, not ready for November; Phase 1 inbox and email-only contact; Black Friday deals bookable | 10-08 Planning: FlightBridge ARC Transfer and Paid-deals Launch |
| [10-08-ai-agent-arc-strategy.md](10-08-ai-agent-arc-strategy.md) | 2026-10-08 | Medium. AI agent trained on Mauricio's Sabre skill; ARC in 3 to 4 weeks; engines by January | 10-08 Meeting: FlightBridge Strategy on AI Agent Development, ARC Approval, and Monetization |
| [09-24-tier-launch-booking-roadmap.md](09-24-tier-launch-booking-roadmap.md) | 09-24 (2026) | High. Most recent booking direction: Book Now Phase 1 and 2, build order, agency model | 09-24 Meeting_ Tiered Travel Subscription Launch, Email Campaign, and Booking Engine Roadmap-transcript.txt |
| [06-10-newsletter-tiers-booking-flow.md](06-10-newsletter-tiers-booking-flow.md) | 06-10 | High. Interim V1 booking form, JourneyFuse phase, booking engine phase | 06-10 Weekly Meeting_ Newsletter Content Strategy, Subscription Tiers, and Booking Flow-transcript.txt |
| [05-22-email-marketing-tool-selection.md](05-22-email-marketing-tool-selection.md) | 05-22 | High. Deal link opens an editable, ready-to-pay booking page | 05-22 Weekly Meeting Flight-Bridge_ Email Marketing Strategy, Tool Selection, and Monetization-transcript.txt; JeffandMauricio.md.md; email_marketing_strategy_tool_selection_and_monotization |
| [05-22-financial-structure.md](05-22-financial-structure.md) | 05-22 | Medium. ARC money flow, Stripe then merchant account | 05-22 Meeting Flight-Bridge_ Financial Structure, Credit Cards, and Payment Processing-transcript.txt; Financial_Structure |
| [05-22-avatar-driven-marketing.md](05-22-avatar-driven-marketing.md) | 05-22 | Low. Payer is often not the traveler | 05-22 Avatar-Driven Marketing Flight-Bridge_ Shifting from Unstable Revenue to a Predictable Sales Model by Targeting the Economic Buyer-transcript.txt; Avatar-Driven Marketing Flight-Bridge |
| [03-16-premium-adventure-experiences.md](03-16-premium-adventure-experiences.md) | 03-16 | Medium. Premium experience packages (monologue, no decisions) | 03-16 From Ideation to Productized Premium Adventure Experiences_ A Decision Framework and Go-To-Market Plan-transcript.txt; Premium Adventure Experiences |
| [12-05-traverse-tech-roadmap.md](12-05-traverse-tech-roadmap.md) | 12-05 (year not stated) | High. Booking tool first, agents do not use the fee portal | 12-05 Strategic Roadmap for Traverse Tech Launch and Growth-transcript.txt |
| [phase-plan-jeff-mauricio.md](phase-plan-jeff-mauricio.md) | Unknown | High. Phase 0/1/2 plan, bookings under Traverse's ARC, AI approach | Mauricio and Jeff Phase Plan-transcript.txt |
| [strategic-vision-unified-platform.md](strategic-vision-unified-platform.md) | Unknown | High. Founding conversation: Sabre, PNR import, online booking tool, fees, segment shares, host agency | Strategic Vision for a Unified Travel Management Platform; Call with Mauricio-transcript.txt |

## Digest format

New digests (written by `/process-transcripts`) must use this layout:

```
---
title: Source Digest - <short title>
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: <YYYY-MM-DD>
source_transcripts: [<every alias filename, exactly as on disk>]
tags: [source-digest, <topics>]
---

# <short title>

**Date:** <MM-DD or Unknown>  **Participants:** <names>
**Aliases:** <list>
**Booking relevance:** High / Medium / Low / None. <one sentence>

## Summary for agents
<3-6 sentences>

## Points
| # | Type | Point | Who | Time | Quote (decisions only) |
|---|------|-------|-----|------|------------------------|

## Topics skipped (not booking)
<one line; these belong to the parent repo>
```
