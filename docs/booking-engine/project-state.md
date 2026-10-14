---
title: "Booking Engine: Project State"
project: Flight Bridge Booking Engine
status: Active
owner: Jeffrey Hammond / Mauricio Melendez
last_updated: 2026-10-13
source_transcripts: [SV, PP, R1205, M0610, M0924, PARENT, M1008P, M1008S]
tags: [project-state, booking-engine]
---

# Booking Engine Project State

## Current Goal

Ship **Phase 1 Book Now**: a lead form on the deal landing page that captures a subscriber's interest in a newsletter deal and routes it to an agent (DEC-BE-006, BE-FB-010). Then build **Phase 2**: real booking on our landing page over Sabre, with agent follow-up (DEC-BE-009).

## Current Phase

Phase 0: Foundation (pre-development). No booking engine code exists yet. See `roadmap.md` for phase definitions (disputed, CONF-BE-004).

## Overall Health

**Not started, direction mostly clear.** The product direction is consistent across sources: newsletter first, booking tool next, B2B later. The blockers are concrete decisions, not unknown direction. Several older decisions were corrected on 2026-10-07 (see `migration-notes.md`).

## Completion Estimate

Unknown. Partners targeted "everything up and running within two years" (R1205 00:02:17). No dates are set for Phase 1 or 2 (Q-BE-009). Phase 2 waits on the ARC transfer, estimated 2 to 4 weeks from 2026-10-08. Mauricio hopes for booking engines by January (ASM-BE-014).

## Current Blockers

1. **Phase 1 inbox address** (CONF-BE-011): info@flytraverse.com or info@flytraverse.com. Blocks building the form.
2. **Token schema** for deal links (Q-BE-007). Blocks form prefill.
3. **ARC transfer** (DEC-BE-014, Q-BE-019). All Sabre and ARC work is on hold until it is done (DEC-BE-015).
4. **Database choice** (Q-BE-003). Blocks Phase 2.
5. **Sabre integration method** (Q-BE-004). Blocks Phase 2.
6. **Payment path** for self-bookings (MI-BE-006, CONF-BE-005). Blocks Phase 2.

## Critical Decisions Pending

- Q-BE-018: official phase numbering and order
- Q-BE-019: legal structure for holding the ARC
- CONF-BE-011: Phase 1 inbox address
- Q-BE-003 / Q-BE-004: database and Sabre method
- Q-BE-008: does the booking engine or the CRM own PNR import?
- DEC-BE-002, DEC-BE-003, DEC-BE-012: marked Needs Review

## Next Milestone

Phase 1 Book Now live on newsletter deals. Relevant timing: the newsletter Basic (flights) tier goes live the first week of November 2026 (PARENT DEC-NL-017). Whether Phase 1 must be live by then has not been stated. Black Friday deals are meant to be bookable from the email, which implies Phase 1 is live before 2026-11-25 (IMP-BE-014). Phase 2 will not be ready for November (DEC-BE-015).

## Immediate Next Actions

1. Jeff confirms the Phase 1 inbox address (CONF-BE-011).
2. Jeff settles the legal structure for the ARC transfer (Q-BE-019).
3. Jeff confirms the phase numbering (Q-BE-018).
4. Jeff defines the deal-link token schema, working with Kit emails (Q-BE-007).
5. Build and test the Phase 1 lead form (BE-FB-010).
6. Jeff researches the Sabre integration options, including Sabre's AI MCP (Q-BE-004, BE-FB-013).
7. Jeff decides SQL vs NoSQL and records it (Q-BE-003).
8. Get Mauricio's wireframes into this repo (MI-BE-008).

## Recent Changes

- **2026-10-13:** processed the two 10-08 transcripts (M1008P, M1008S). ARC transfer agreed (DEC-BE-014); engine work on hold until then (DEC-BE-015); Phase 1 contact is email only; JourneyFuse affiliate tracking (DEC-BE-016); inbox address disputed (CONF-BE-011); new risks RISK-BE-015 to 017.
- **2026-10-13:** Mauricio and his AI tool Viktor monitor info@flytraverse.com. Q-BE-010 resolved; Phase 1 routing is settled.
- **2026-10-12:** Phase 1 lead destination set to info@flytraverse.com (Jeff). CONF-BE-007 resolved; Q-BE-010 narrowed to who watches the inbox.
- **2026-10-07:** repo split from the parent Flight-Bridge repo. All transcripts re-read for booking content. The 06-10 and 09-24 meetings' booking content was captured for the first time (DEC-BE-006 to 009, REQ-BE-008 to 012). DEC-BE-002, 003 and 005 were corrected against their transcript. See `migration-notes.md`.
- **2026-09-30:** newsletter free tier launched (PARENT)
- **2026-09-24:** Book Now Phase 1 / Phase 2 defined; build order and agency model agreed (M0924)

## Last Review Date

2026-10-13
